<template>
    <ion-page>
        <!-- <ion-header>
          <ion-toolbar>
            <HeaderComponent />
          </ion-toolbar>
        </ion-header> -->

        <ion-content>
            <div class="mx-4 mt-8 tablet:mx-8">  
                <div class="h-[74px]"></div> 
                    <div>
                        <transition-group 
                        class="grid 
                        grid-cols-2 
                        gap-4 
                        tablet:grid-cols-4 
                        lg-table:grid-cols-5 
                        laptop:grid-cols-4
                        mb-8"
                        name="showList" tag="div">
                        <div @click="routeToshow(shows.id)" v-for="(shows, index) in showStore.shows" :key="index" 
                            class="col-span-1 cursor-pointer group">
                                <div class="inline-block laptop:h-full laptop:shadow-card-shadow">
                                    <div class="flex 
                                    flex-col 
                                    gap-y-2
                                    laptop:items-center
                                    laptop:bg-gradient-to-t from-[#292929] to-[#121212]
                                    group-hover:to-60%
                                    transition
                                    duration-500
                                    laptop:rounded-[10px]
                                    laptop:p-4
                                    laptop:h-full">
                                        <div 
                                        class="w-[152px] laptop:w-[174px] 
                                        aspect-square 
                                        overflow-hidden 
                                        rounded-[10px]
                                        shadow-card-shadow">
                                            <img class="w-full h-full" :src="shows.cover_img" alt="">
                                        </div>

                                        <div class="flex flex-col ">
                                            <div class="flex items-center gap-x-1">
                                                <span class="text-x-sm text-white/60 font-semibold">{{ shows.totalEpisodes }} Episodes</span>
                                                <div>
                                                    <svg width="5" height="4" viewBox="0 0 5 4" fill="none" xmlns="http://www.w3.org/2000/svg">
                                                        <circle cx="2.04778" cy="2" r="2" fill="#E84344"/>
                                                    </svg>
                                                </div>
                                                <span class="text-x-sm text-white/60 font-semibold">{{ shows.listener_count }} listen</span>
                                            </div>

                                            <span  class="text-white text-base font-medium laptop:w-[174px]">
                                                {{ shows.title }}
                                            </span>
                                        </div>
                                    </div>
                                </div>

                            </div>
                        </transition-group>


                </div>
            </div>
        </ion-content>
    </ion-page>
</template>


<script setup>
import { onMounted } from 'vue';
import { useShowsStore } from '../stores/ShowsStore';
import { useForumStore } from '../stores/forumStore';
import { useRouter } from 'vue-router';
import { IonPage, IonContent } from '@ionic/vue';
// import HeaderComponent from './HeaderComponent.vue';

const showStore = useShowsStore();
const forumStore = useForumStore();
const router = useRouter();

onMounted(async () => {

if (!showStore.shows.length) {

    showStore.fetchShows();

    }

if (!forumStore.forums.length)
{
    await forumStore.getForums();

        }
    })

function routeToshow(showid) {
    router.push({
        name : 'show',
        params : {
            id : showid
        }
    })
}

</script>

<style>

</style>