<template>
  <ion-page>
    <div style="overflow-y:scroll;margin-bottom:80px;">
      <ion-text>
        <h1 class="font-sans text-2xl mt-10 ml-5 text-black font-bold">Welcome</h1>
        <p class="font-sans text-xs ml-5 text-black font-bold">Since, this is your first and last birthday in our collage, Here are your favourite BTS songs</p>
      </ion-text>
      <ion-searchbar :search-icon="searchOutline" class="mt-5 searchbar" show-cancel-button="always"></ion-searchbar>
      <ion-card class="rounded-lg mt-5 white" v-for="song in data" :key="song.id">
        <ion-item :href='"/song/"+song.id'>
          
          <ion-avatar slot="start">
            <img src="./../../public/assets/bts_logo.jpg">
          </ion-avatar>
          <ion-label><p class="text-black font-bold">{{song.name}}</p><p>{{song.artist}}</p></ion-label>
        </ion-item>
      </ion-card>
    </div>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage, IonSearchbar, IonText, IonCard , IonItem, IonLabel} from '@ionic/vue';
import { searchOutline, home, pin } from 'ionicons/icons';

export default  defineComponent({
  name: 'Tab1Page',
  components: { IonPage, IonSearchbar, IonText, IonCard, IonItem, IonLabel },
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
            {"id": 1, "path": "", "name": "FESTA Euphoria", "artist": "BTS", "logo": "./../../public/assets/bts_logo.jpg"},
            {"id": 2, "path": "", "name": "Best of me", "artist": "BTS", "logo": "./../../public/assets/bts_logo.jpg"},
            {"id": 3, "path": "", "name": "Blood sweat and tears", "artist": "BTS", "logo": "./../../public/assets/bts_logo.jpg"},
            {"id": 4, "path": "", "name": "Fake love", "artist": "BTS", "logo": "./../../public/assets/bts_logo.jpg"},
            {"id": 5, "path": "", "name": "Fire", "artist": "BTS", "logo": "./../../public/assets/bts_logo.jpg"},
            {"id": 6, "path": "", "name": "Magic shop", "artist": "BTS", "logo": "./../../public/assets/bts_logo.jpg"},
            {"id": 7, "path": "", "name": "Love myself", "artist": "BTS", "logo": "./../../public/assets/bts_logo.jpg"},
            {"id": 8, "path": "", "name": "Black swan", "artist": "BTS", "logo": "./../../public/assets/bts_logo.jpg"},
            {"id": 9, "path": "", "name": "Love yourself", "artist": "BTS", "logo": "./../../public/assets/bts_logo.jpg"},
            {"id": 10, "path": "", "name": "Spring day", "artist": "BTS", "logo": "./../../public/assets/bts_logo.jpg"}
          ]
  }),
  methods: {
    updateSelected(val:number){
      this.selected = val;
    }
  }
});
</script>
