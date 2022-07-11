<template>
    <ion-page>
        <div style="overflow-y:scroll;margin-bottom: 50px;">
            <ion-toolbar>
                <ion-buttons slot="start">
                    <ion-button href="/memories">
                        <ion-icon slot="icon-only" style="color:black;" :icon="chevronBackOutline"></ion-icon>
                    </ion-button>
                </ion-buttons>
                <ion-title><h1 class="text-center font-sans text-black font-bold">Memory</h1></ion-title>
                <ion-buttons slot="end">
                    <ion-button>
                        <ion-icon slot="icon-only" style="color:black;" :icon="gridOutline"></ion-icon>
                    </ion-button>
                </ion-buttons>
            </ion-toolbar>
            <ion-card>
                <ion-card-content>
                    <img :src='"./assets/images/" + id.toString() + ".jpeg"'/>
                </ion-card-content>
            </ion-card>
        </div>
    </ion-page>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import { useRoute } from 'vue-router'
import { IonPage, IonTitle, IonToolbar, IonIcon, IonCard, IonCardContent,  } from '@ionic/vue';
import { chevronBackOutline, gridOutline } from 'ionicons/icons';

export default defineComponent({
    beforeMount(){
        const route = useRoute();
        this.id = parseInt(route.params.id.toString());
    },
    name: 'PhotoPage',
    components: { IonPage, IonTitle, IonToolbar, IonCard, IonCardContent, IonIcon },
    setup() {
        let id = ref(1);
        return {
            chevronBackOutline,
            gridOutline,
            id
        }
    },
});

</script>
