<template>
    <div class="home">
        <img class="center" style="margin-top:100px" width="300" height="300" src="/assets/home.svg"/>
        <h1 class="text-center mt-16 font-sans text-3xl font-bold">Kareddy Harshitha</h1>
        <p class="mx-6 text-center mt-4 font-sans text-base font-semibold">
            May the joy that you have spread in the past come back to you on this day. Wishing you a very
        </p>
        <div class="center">
            <ion-button href="/tabs/tab1" type="button" size="large" class="home-button">Happy Birthday →</ion-button>
        </div>
    </div>
</template>

<style scoped>
.center {
    display: block;
    margin: 0 auto;
    text-align: center;
}

.home{
    position: absolute /*relative and fixed elements also works*/;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: #fed7aa;
}

</style>

<script lang="ts">
import { IonButton } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'HomePage',
    components: { IonButton },
});
</script>

