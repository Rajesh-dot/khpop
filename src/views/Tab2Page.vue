<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title class="text-black">Tab 2</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title class="text-black" size="large">Comming Soon</ion-title>
        </ion-toolbar>
      </ion-header>
      <h1>Comming Soon</h1>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';

export default defineComponent({
  name: 'Tab2Page',
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage }
});
</script>
