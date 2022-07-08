<template>
    <ion-page>
        <div>
            <ion-toolbar>
                <ion-buttons slot="start">
                    <ion-button>
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
            <ion-card class="rounded-2xl h-full mt-8">
                <img class="h-4/6" src="https://c4.wallpaperflare.com/wallpaper/14/548/927/the-avengers-avengers-endgame-avengers-endgame-infinity-gauntlet-iron-man-hd-wallpaper-preview.jpg" />
                <ion-card-header>
                    
                </ion-card-header>
                <ion-card-content>
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
import { defineComponent } from 'vue';
import { IonPage, IonCard, IonButton, IonButtons, IonCardContent, IonCardHeader, IonToolbar, IonTitle, IonIcon, IonRange } from '@ionic/vue';
import { chevronBackOutline, gridOutline, playOutline, pauseOutline, playBack, playForward, repeatOutline, shuffleOutline } from 'ionicons/icons';

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
        play: true
    }),
    methods: {
        toggle(){
            this.play = !this.play;
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
}

ion-range {
    --bar-background: #a2d2ff;
    --bar-background-active: #bde0fe;
    --bar-height: 8px;
    --bar-border-radius: 8px;
    --knob-background: #ffc8dd;
    --knob-size: 40px;
    --pin-background: #ffafcc;
    --pin-color: #fff;
}

</style>