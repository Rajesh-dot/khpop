<template>
  <ion-page>
    <div>
      <ion-header>
        <ion-toolbar>
          <ion-title class="text-black">Favourites</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-card class="rounded-lg mt-5">
        <ion-item href='/memories'>
          <ion-icon style="color:black" class="mr-3" :icon="happyOutline"></ion-icon>
          <ion-label><p class="text-black font-bold ml-2">Memories</p></ion-label>
        </ion-item>
      </ion-card>
    </div>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonItem, IonLabel, IonCard, IonIcon } from '@ionic/vue';
import { happyOutline } from 'ionicons/icons';

export default defineComponent({
  name: 'Tab3Page',
  components: { IonHeader, IonToolbar, IonTitle, IonPage, IonItem, IonLabel, IonCard, IonIcon },
  setup() {
    return {
        happyOutline
    }
  },
});
</script>
