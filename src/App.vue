
<template>

  <ion-app>
        <ion-header>
            <ion-toolbar>
                <HeaderComponent />
            </ion-toolbar>
        </ion-header>

        <div v-if="notiStore.hasMessage" :class="[(notiStore.type === 'info' || notiStore.type === 'complete' || notiStore.type === 'progress') ? 'bg-white' : 'bg-[#FF0F00]/40']" class="fixed bottom-8 left-8 p-1 z-[9999] rounded-[15px] transition-all">
            
          <span class="text-[#35A519] font-medium text-sm">{{ notiStore.message }}</span>
        
        </div>

        <div>
          <ion-router-outlet />
        </div>
        <transition appear>
          <SongComponent v-show="showStore.currentEpisode.title"/>      
        </transition>
  </ion-app>

  <Teleport to="body">
        <transition name="modal">
        
            <div v-if="searchStore.openSearch" class="modal-mask">
                <div class="modal-container-search rounded-[15px] relative">
                    <button @click="searchStore.openSearch = false; searchStore.episodes = []" class="absolute left-2 top-2 group" type="button">
                      <div class="w-8 h-8">
                        <svg class="w-full h-full" viewBox="0 0 17 18" fill="none" xmlns="http://www.w3.org/2000/svg">
                          <path d="M6.2376 11.2624L8.5008 9ZM10.7632 6.7376L8.5008 9ZM8.5008 9L6.2376 6.7376ZM8.5008 9L10.7632 11.2624ZM8.5 17C12.9184 17 16.5 13.4184 16.5 9C16.5 4.5816 12.9184 1 8.5 1C4.0816 1 0.5 4.5816 0.5 9C0.5 13.4184 4.0816 17 8.5 17Z" class="fill-white/10 group-hover:fill-white/20 group-active:fill-white/10"/>
                          <path d="M6.2376 11.2624L8.5008 9M8.5008 9L10.7632 6.7376M8.5008 9L6.2376 6.7376M8.5008 9L10.7632 11.2624M8.5 17C12.9184 17 16.5 13.4184 16.5 9C16.5 4.5816 12.9184 1 8.5 1C4.0816 1 0.5 4.5816 0.5 9C0.5 13.4184 4.0816 17 8.5 17Z" class="stroke-white/60" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                      </div>
                    </button>
                    
                    <h1 class="modal-header mb-4 text-white/80 text-lg font-semibold text-center">search</h1>
                      <div>
                        <SearchComponent />
                      </div>
                </div>
            </div>                
        </transition>

  </Teleport>

</template>

<script setup>
import {useSearchStore} from './stores/searchStore';
import SearchComponent from './components/SearchComponent.vue';
import { useNotificationStore } from './stores/NotiStore';
import { onMounted, ref } from 'vue';
import { useShowsStore } from './stores/ShowsStore';
import SongComponent from './components/SongComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';
import { IonApp, IonRouterOutlet, IonHeader, IonToolbar } from '@ionic/vue'; 

const searchStore = useSearchStore();
const notiStore = useNotificationStore();
const showStore = useShowsStore();

const height = ref();

onMounted(() => {
  height.value = window.clientHeight - 120;
})

navigator.serviceWorker.addEventListener('message', (event) => {
  const { type, progress } = event.data;

  if (type === 'progress') {
    notiStore.showNotification(`Saving ${progress}%`, type);
  } else if (type === 'complete') {
    notiStore.showNotification('Saved to playList, Listen offline now', type);
  }

  
})

</script>



<style scoped>

</style>
