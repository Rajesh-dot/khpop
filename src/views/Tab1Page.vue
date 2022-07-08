<template>
  <ion-page>
    <div>
      <ion-text>
        <h1 class="font-sans text-2xl mt-10 ml-5 text-black font-bold">Welcome</h1>
        <p class="font-sans text-xs ml-5 text-black font-bold">Since, this is your first and last birthday in our collage, Here are your favourite BTS songs</p>
      </ion-text>
      <ion-searchbar class="rounded-full mt-5" show-cancel-button="always"></ion-searchbar>
      <ion-card class="rounded-lg mt-5" v-for="song in data" :key="song.id">
        <ion-item href="/song/">
          <ion-icon :icon="pin" slot="start"></ion-icon>
          <ion-label><p class="text-black font-bold">song.name</p><p>song.artist</p></ion-label>
        </ion-item>
      </ion-card>
    </div>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage, IonSearchbar, IonText } from '@ionic/vue';
import { searchOutline, home, pin } from 'ionicons/icons';

export default  defineComponent({
  name: 'Tab1Page',
  components: { IonPage, IonSearchbar, IonText },
  setup() {
    return {
      searchOutline,
      home,
      pin
    }
  },
  data: () => ({
    selected: 1,
    data: [
            {id: 1, name: "Butter", artist: "BTS"},
            {id: 2, name: "Cheese", artist: "BTS"},
            {id: 3, name: "Honey", artist: "BTS"},
            {id: 4, name: "Milk", artist: "BTS"}
          ]
  }),
  methods: {
    updateSelected(val:number){
      this.selected = val;
    }
  }
});
</script>
