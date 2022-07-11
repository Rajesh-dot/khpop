<template>
  <ion-page>
    <div style="overflow-y:scroll;margin-bottom: 50px;">
        <ion-card class="mt-5 font-sans text-black font-bold">
            <ion-card-header>
                <h1></h1>
            </ion-card-header>
            <ion-card-content>
                <ion-text>
                    <h1 class="font-sans text-2xl mt-10 ml-5 text-black font-bold">Hello,</h1>
                    <p class="font-sans ml-5 mr-3 text-black font-bold">This is a little gift from your beloved friend Rajesh, hope this can preserve your memories(Fav/memories) of Btech along with your friends for-ever</p>
                </ion-text>
            </ion-card-content>
        </ion-card>
        <ion-card class="mt-5 font-sans text-black">
            <ion-card-header class="">
                <h1 class="font-sans text-center text-lg text-black">If you know you know</h1>
            </ion-card-header>
            <ion-card-content>
                <img src="./../../public/assets/magic.png" />
                <h3 class="font-sans text-black ml-6 mt-4 pt-3">Hint:- Magic square</h3>
            </ion-card-content>
        </ion-card>
        <ion-card class="mt-10 font-sans text-black font-bold">
            <ion-card-header class="">
                <h1 class="font-sans text-center text-lg text-black font-bold">Note</h1>
            </ion-card-header>
            <ion-card-content>
                <h2 class="font-sans text-black ml-6 mt-4 pt-3" style="font-style: bold">This this is made as a fun project and not production ready yet, so updates will be comming now and then. If there are any updates they will be notified here.</h2>
                <h2 class="font-sans text-black ml-6 mb-2 pb-2" style="font-style: bold">Fun fact:- KHPOP = Kareddy Harshitha pop</h2>
                <ion-button href="https://github.com/Rajesh-dot"><ion-icon slot="icon-only" :icon="logoGithub"></ion-icon></ion-button>
            </ion-card-content>
        </ion-card>
        <h2 class="mt-5 mb-7 font-sans text-black text-center font-bold">©KaipaRajesh-2022</h2>
    </div>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage, IonCard, IonCardContent, IonCardHeader, IonText } from '@ionic/vue';
import { logoGithub } from 'ionicons/icons';

export default defineComponent({
  name: 'Tab4Page',
  components: { IonPage, IonCard, IonCardContent, IonCardHeader, IonText },
  setup() {
    return {
        logoGithub
    }
  },
});
</script>
