<template>

    <ion-page>

        <ion-content>
            <div class="w-full flex flex-col min-h-screen justify-between" id="cover">
                <div class="h-[74px]"></div>
                <div class="laptop:p-16 p-4 flex flex-col justify-between gap-y-8 text-x-lg h-full laptop:flex laptop:flex-col laptop:gap-y-12 laptop:items-start laptop:gap-x-4 laptop:justify-evenly">
                        <div class="relative">
                            <i class="text-white/80 text-x-lg font-semibold uppercase">Why</i>

                            <div  class="relative">
                                <p class="text-white text-base not-italic z-[999]">
                                    Burma Podcast Network exist to make a collective social impact through podcasting. We collaborate with amazing people from different professions for colorful ideas and life stories. 
                            
                                </p>

                            </div>
                        </div>
                        <div class="relative">
                            <i class="text-white/80 text-x-lg font-semibold uppercase">How</i>

                            <div class="relative">
                            
                                <i class="text-white text-base not-italic">
                                    Burma Podcast is dedicated to promote various podcasts from Myanmar podcasters in one place. Our listeners can easily access their favorite show or episode and contribute their favorite podcasters earn listenership. 
                                </i> 

                            </div>
                        </div>
                        <div class="relative">
                            <i class="text-white/80 text-x-lg font-semibold uppercase">Who</i>
                            <div class="relative">
                                <i class="text-white text-base">
                                    Burma Podcast Network is founded by two young men who love to think , talk and listen human&apos;s stories. 
                                </i>
                            </div>
                        </div>
                    </div>

                <div class="flex gap-x-4 justify-center mx-16 pb-12 tablet:block">
                    <h1 class="text-[#E84344] text-x-lg font-semibold italic text-shadow tablet:block">Think</h1>
                    <h1 class="text-[#E84344] text-x-lg font-semibold italic text-shadow tablet:block">Talk</h1>
                    <h1 class="text-[#E84344] text-x-lg font-semibold italic text-shadow tablet:block">Listen</h1>
                </div>
            
                <FooterComponent />
            </div>
        </ion-content>

    </ion-page>
</template>


<script setup>
import { IonPage, IonContent } from '@ionic/vue';
// import HeaderComponent from './HeaderComponent.vue';
import FooterComponent from './FooterComponent.vue';

</script>

<style>

/* #cover {
    background-image: url(../assets/aboutuscover.jpeg);
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    background-blend-mode: darken;
} */

.text-shadow {
    text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.80); 
}

</style>