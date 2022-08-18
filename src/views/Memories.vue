<template>
    <ion-page>
        <div style="overflow-y:scroll;margin-bottom: 50px;">
            <ion-header>
                <ion-toolbar>
                    <ion-title class="text-black">Memories</ion-title>
                </ion-toolbar>
            </ion-header>
            <ion-grid>
                <ion-row v-for="n in 31" :key="n">
                    <ion-col>
                        <ion-card :href='"image/"+(3*(n-1)+1).toString()' class="rounded-lg">
                            <ion-card-content>
                                <img class="w-full h-40" :src='"./assets/images/" + (3*(n-1)+1).toString() + ".jpeg"' />
                            </ion-card-content>
                        </ion-card>
                    </ion-col>
                    <ion-col>
                        <ion-card :href='"image/"+(3*(n-1)+2).toString()' class="rounded-lg">
                            <ion-card-content>
                                <img class="w-full h-40" :src='"./assets/images/" + (3*(n-1)+2).toString() + ".jpeg"' />
                            </ion-card-content>
                        </ion-card>
                    </ion-col>
                    <ion-col>
                        <ion-card :href='"image/"+(3*(n-1)+3).toString()' class="rounded-lg">
                            <ion-card-content>
                                <img class="w-full h-40" :src='"./assets/images/" + (3*(n-1)+3).toString() + ".jpeg"' />
                            </ion-card-content>
                        </ion-card>
                    </ion-col>
                </ion-row>
            </ion-grid>
        </div>
    </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonPage, IonHeader, IonTitle, IonToolbar, IonGrid, IonRow, IonCol, IonCard, IonCardContent,  } from '@ionic/vue';
import { logoGithub } from 'ionicons/icons';

export default defineComponent({
  name: 'MemoriesPage',
  components: { IonPage, IonHeader, IonTitle, IonToolbar, IonCard, IonGrid, IonRow, IonCol, IonCardContent },
  setup() {
    return {
        logoGithub
    }
  },
});

</script>

