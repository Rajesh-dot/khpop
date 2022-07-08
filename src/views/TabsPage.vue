<template>
  <ion-page class="white">
    <ion-tabs class="white">
      <ion-router-outlet></ion-router-outlet>
      <ion-fab vertical="bottom" horizontal="center" slot="fixed" translucent="true">
        <ion-fab-button ion-fixed href="/add_new" color="dark">
          <ion-icon :icon="addOutline"/>
        </ion-fab-button>
      </ion-fab>
      <ion-tab-bar slot="bottom">

        <ion-tab-button tab="tab1" @click="updateSelected(1)" href="/tabs/tab1">
          <ion-icon :icon="home" />
          <ion-label>Home</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab2" @click="updateSelected(2)" href="/tabs/tab2">
          <ion-icon :icon="library" />
          <ion-label>Library</ion-label>
        </ion-tab-button>

        <svg class="svg-class" height="50" viewBox="0 0 100 50" width="100" xmlns="http://www.w3.org/2000/svg"><path class="path-class" d="M100 0v50H0V0c.543 27.153 22.72 49 50 49S99.457 27.153 99.99 0h.01z" fill="white" fill-rule="evenodd"></path></svg>
      
        <ion-tab-button tab="tab3" @click="updateSelected(3)" href="/tabs/tab3">
          <ion-icon :icon="musicalNote" />
          <ion-label>Fav</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab4" @click="updateSelected(4)" href="/tabs/tab4">
          <ion-icon :icon="analytics" />
          <ion-label>About</ion-label>
        </ion-tab-button>

      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage, IonRouterOutlet, IonFab, IonFabButton } from '@ionic/vue';
import { addOutline, home, library, musicalNote, analytics } from 'ionicons/icons';

export default defineComponent({
  name: 'TabsPage',
  components: { IonLabel, IonTabs, IonTabBar, IonTabButton, IonIcon, IonPage, IonRouterOutlet, IonFab, IonFabButton },
  setup() {
    return {
      addOutline, 
      home,
      library,
      musicalNote,
      analytics
    }
  },
  data: () => ({
    selected: 1,
  }),
  methods: {
    updateSelected(val:number){
      this.selected = val;
    }
  }
});
</script>
