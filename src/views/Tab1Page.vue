<template>
  <ion-page>
    <ion-searchbar class="rounded-full" show-cancel-button="always"></ion-searchbar>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage } from '@ionic/vue';
import { searchOutline, home } from 'ionicons/icons';

export default  defineComponent({
  name: 'Tab1Page',
  components: { IonPage },
  setup() {
    return {
      searchOutline,
      home
    }
  },
});
</script>
