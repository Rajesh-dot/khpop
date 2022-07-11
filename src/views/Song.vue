<template>
    <ion-page>
        <div style="overflow-y:scroll;">
            <ion-toolbar>
                <ion-buttons slot="start">
                    <ion-button href="/tabs/tab1">
                        <ion-icon slot="icon-only" style="color:black;" :icon="chevronBackOutline"></ion-icon>
                    </ion-button>
                </ion-buttons>
                <ion-title><h1 class="text-center font-sans text-black font-bold">KHPOP</h1></ion-title>
                <ion-buttons slot="end">
                    <ion-button>
                        <ion-icon slot="icon-only" style="color:black;" :icon="gridOutline"></ion-icon>
                    </ion-button>
                </ion-buttons>
            </ion-toolbar>
            <ion-card class="rounded-2xl mt-4">
                <img class="w-full h-80" src="./../../public/assets/bts_logo.jpg" />
                <ion-card-header>
                    <h1 class="text-black text-center text-2xl">{{name}}</h1>
                </ion-card-header>
                <ion-card-content class="pb-8">
                    <span style="font-size:12px;display:inline-block;">{{current}}</span>
                    <span style="float: right;font-size: 12px;">{{duration}}</span>
                    <ion-range v-model="progress" max="100" @touchend="seek()" @mouseup="seek()"></ion-range>
                    <ion-buttons class="mb-6">
                        <ion-buttons slot="start">
                            <ion-button class="big" size="large">
                                <ion-icon slot="icon-only" :icon="shuffleOutline"></ion-icon>
                            </ion-button>
                        </ion-buttons>
                        <ion-buttons @click="prev" slot="primary">
                            <ion-button class="big" size="large">
                                <ion-icon slot="icon-only" :icon="playBack"></ion-icon>
                            </ion-button>
                        </ion-buttons>
                        <ion-buttons class="center">
                            <ion-button @click="toggle" class="big" size="large">
                                <ion-icon v-if="!play" slot="icon-only" :icon="playOutline"></ion-icon>
                                <ion-icon v-else slot="icon-only" :icon="pauseOutline"></ion-icon>
                            </ion-button>
                        </ion-buttons>
                        <ion-buttons slot="secondary">
                            <ion-button @click="next" class="big" size="large">
                                <ion-icon slot="icon-only" :icon="playForward"></ion-icon>
                            </ion-button>
                        </ion-buttons>
                        <ion-buttons slot="end">
                            <ion-button @click="()=>{loop=!loop}" class="big" size="large">
                                <ion-icon v-if="loop" slot="icon-only" style="color:green" :icon="repeat"></ion-icon>
                                <ion-icon v-else slot="icon-only" :icon="repeatOutline"></ion-icon>
                            </ion-button>
                        </ion-buttons>
                    </ion-buttons>
                </ion-card-content>
            </ion-card>
        </div>
    </ion-page>
</template>


<script lang="ts">
import { defineComponent, ref, } from 'vue';
import { useRoute } from 'vue-router'
import { IonPage, IonCard, IonButton, IonButtons, IonCardContent, IonCardHeader, IonToolbar, IonTitle, IonIcon, IonRange } from '@ionic/vue';
import { chevronBackOutline, gridOutline, playOutline, pauseOutline, playBack, playForward, repeatOutline, shuffleOutline, repeat } from 'ionicons/icons';
import { Howl } from 'howler';
import data from "../composables/Audio";
const songs = {data};


export default defineComponent({
    mounted(){
        this.updateProgress();
    },
    beforeMount(){
        const route = useRoute();
        this.id = parseInt(route.params.id.toString());
    },
    created(){
        const route = useRoute();
        this.id = parseInt(route.params.id.toString());
        this.update(this.id);
        this.start(this.id);
    },
    name: 'SongPage',
    components: { IonPage, IonCard, IonButton, IonButtons, IonCardContent, IonCardHeader, IonIcon,IonToolbar, IonTitle, IonRange },
    setup() {
        let player = ref();
        let play = ref(false);
        let id = ref(0);
        let activeTrack = ref(0);
        let progress = ref(0);
        let current = ref("0:00");
        let duration = ref("0:00");
        let loop = ref(false);
        let image = ref("");
        let name = ref("");
        function start(id:number){
            player.value = new Howl({
                src: ['./assets/files/' + id.toString() + ".mp3"],
                onplay: () => {
                    activeTrack.value = id;
                },
                onend: () => {
                    if(loop.value){
                        player.value.play();
                    }
                    else{
                        id = (id)%10+1;
                        update(id);
                        start(id);
                    }
                }
            })
            player.value.play();
            play.value = true;
            updateProgress();
        }
        function toggle(){
            if(play.value){
                player.value.pause();
            }
            else{
                player.value.play();
            }
            play.value = !play.value;
        }
        function next(){
            player.value.stop();
            id.value = (id.value)%10+1;
            update(id.value);
            start(id.value);
        }
        function prev(){
            player.value.stop();
            id.value = (id.value+8)%10+1;
            update(id.value);
            start(id.value);
        }
        function seek(){
            let duration:number = player.value.duration();
            player.value.seek(duration*(progress.value/100));
            current.value = formatTime(player.value.seek());
        }
        function updateProgress(){
            let seek = player.value.seek();
            progress.value = (seek/player.value.duration())*100 || 0;
            current.value = formatTime(player.value.seek());
            duration.value = formatTime(player.value.duration());
            setTimeout(()=>{
                updateProgress();
            },1000);
        }
        function formatTime(secs:number) {
            var minutes = Math.floor(secs / 60) || 0;
            var seconds = Math.floor(secs - minutes * 60) || 0;
            return (minutes < 10 ? '0' : '') + minutes + ':' + (seconds < 10 ? '0' : '') + seconds;
        }
        function update(new_id:number){
            id.value = new_id;
            name.value = songs.data.songs[new_id-1].name;
        }
        return {
            chevronBackOutline,
            gridOutline,
            playOutline,
            pauseOutline,
            playBack,
            playForward,
            repeatOutline,
            shuffleOutline,
            repeat,
            play,
            id,
            activeTrack,
            progress,
            current,
            duration,
            loop,
            image,
            name,
            seek,
            next,
            prev,
            toggle,
            start,
            updateProgress,
            update,
        }
    }
});

</script>


<style scoped>
.center {
    display: block;
    margin: 0 auto;
    text-align: center;
}

.big {
    height:96px;
    width:96px;
    color: black;
}

ion-range {
    --bar-background: #a2d2ff;
    --bar-background-active: #bde0fe;
    --bar-height: 6px;
    --bar-border-radius: 8px;
    --knob-background: #fed7aa;
    --knob-size: 30px;
    --pin-background: #ffafcc;
    --pin-color: #fff;
}


</style>