<template>
    <ion-page>
        <div>
            <ion-toolbar>
                <ion-buttons slot="start">
                    <ion-button href="/tabs/tab1">
                        <ion-icon slot="icon-only" :icon="chevronBackOutline"></ion-icon>
                    </ion-button>
                </ion-buttons>
                <ion-title><h1 class="text-center font-sans text-black font-bold">KHPOP</h1></ion-title>
                <ion-buttons slot="end">
                    <ion-button>
                        <ion-icon slot="icon-only" :icon="gridOutline"></ion-icon>
                    </ion-button>
                </ion-buttons>
            </ion-toolbar>
            <ion-card class="rounded-2xl h-full mt-6">
                <img class="w-full h-80" src="https://m.media-amazon.com/images/I/51qNgkExM8L._SX522_.jpg" />
                <ion-card-header>
                    
                </ion-card-header>
                <ion-card-content>
                    <span style="font-size:12px;display:inline-block;">0:00</span>
                    <span style="float: right;font-size: 12px;">11:00</span>
                    <ion-range></ion-range>
                    <ion-buttons>
                        <ion-buttons slot="start">
                            <ion-button class="big" size="large">
                                <ion-icon slot="icon-only" :icon="shuffleOutline"></ion-icon>
                            </ion-button>
                        </ion-buttons>
                        <ion-buttons slot="primary">
                            <ion-button class="big" size="large">
                                <ion-icon slot="icon-only" :icon="playBack"></ion-icon>
                            </ion-button>
                        </ion-buttons>
                        <ion-buttons class="center">
                            <ion-button @click="toggle" class="big" size="large">
                                <ion-icon v-if="play" slot="icon-only" :icon="playOutline"></ion-icon>
                                <ion-icon v-else slot="icon-only" :icon="pauseOutline"></ion-icon>
                            </ion-button>
                        </ion-buttons>
                        <ion-buttons slot="secondary">
                            <ion-button class="big" size="large">
                                <ion-icon slot="icon-only" :icon="playForward"></ion-icon>
                            </ion-button>
                        </ion-buttons>
                        <ion-buttons slot="end">
                            <ion-button class="big" size="large">
                                <ion-icon slot="icon-only" :icon="repeatOutline"></ion-icon>
                            </ion-button>
                        </ion-buttons>
                    </ion-buttons>
                </ion-card-content>
            </ion-card>
        </div>
    </ion-page>
</template>


<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';
import { IonPage, IonCard, IonButton, IonButtons, IonCardContent, IonCardHeader, IonToolbar, IonTitle, IonIcon, IonRange } from '@ionic/vue';
import { chevronBackOutline, gridOutline, playOutline, pauseOutline, playBack, playForward, repeatOutline, shuffleOutline } from 'ionicons/icons';
import { Howl } from 'howler';

const el = ref()

onMounted(() => {
  el.value // <div>
})

export default defineComponent({
    name: 'SongPage',
    components: { IonPage, IonCard, IonButton, IonButtons, IonCardContent, IonCardHeader, IonIcon,IonToolbar, IonTitle, IonRange },
    setup() {
        return {
            chevronBackOutline,
            gridOutline,
            playOutline,
            pauseOutline,
            playBack,
            playForward,
            repeatOutline,
            shuffleOutline
        }
    },
    data: () => ({
        play: true,
        player: new Howl({
                src: ['./assets/files/song.mp3']
            }),
        activeTrack: 0,
    }),
    methods: {
        start(id:number){
            this.player = new Howl({
                src: ['./assets/files/song.mp3'],
                onplay: () => {
                    this.play = true;
                    this.activeTrack = id;
                },
                onend: () => {
                    console.log("hello")
                }
            })
            this.player.play();
        },
        toggle(){
            this.play = !this.play;
            if(this.play){
                this.player.pause();
            }
            else{
                this.player.play();
            }
        },
        next(){
            console.log("hello");
        },
        prev(){
            console.log("hello");
        },
        seek(){
            console.log("hello");
        },
        updateProgress(){
            console.log("hello");
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
    --bar-height: 8px;
    --bar-border-radius: 8px;
    --knob-background: #fed7aa;
    --knob-size: 40px;
    --pin-background: #ffafcc;
    --pin-color: #fff;
}


</style>