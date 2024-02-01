<script setup lang="ts">
import { ref } from 'vue';
import { useMediaQuery } from '@vueuse/core'
import Roulette from './components/Roulette.vue';
import Parallax from './components/Parallax.vue';
import Prize from './components/Prize.vue';

const spiningDelay = 5300;
const showYourWin = 1300;
const showYourWinShow = 500;

const isMobileL = useMediaQuery('(min-width: 880px)');

const spinCount = ref(2);
const rouletteSpin = ref(false);
const isShowYourWin = ref(false);
const isShowYourWinShow = ref(false);

const spinPlay = () => {
  if (!rouletteSpin.value) {
    rouletteSpin.value = true;

    setTimeout(() => {
      rouletteSpin.value = false; 

      if (spinCount.value) {
        spinCount.value--;
      }

      setTimeout(() => {
        if (!spinCount.value) {          
          isShowYourWin.value = true;

          setTimeout(() => {
            isShowYourWinShow.value = true;
          }, showYourWinShow);
        }
      }, showYourWin);
    }, spiningDelay);
  }
}

</script>

<template>
  <div class="relative max-w-[1400px] w-full mx-auto pt-6 px-5 text-white z-10">
    <div class="relative mb-5 z-10 tablet:mb-8 mobile-l:mb-3">
      <a href="#" class="block max-w-[195px] mb-2 mx-auto mobile-l:max-w-[128px] mobile-l:mb-[6px]">
        <img src="./assets/images/logo.png" alt="logo">
      </a>
      <h1 class="text-[28px] leading-[1.4] font-bold text-white text-center mobile-l:text-base">
        БОНУС ДО 
        <span class=" text-[#DFB778]">35 000 РУБ</span> 
        НОВЫМ ИГРОКАМ!
      </h1>
    </div>  
    <div class="roulette-center flex flex-col justify-between items-center tablet:flex-row">
      <Prize 
        :spinCount="spinCount"
      />
      <Roulette
        :spinCount="spinCount"
        :rouletteSpin="rouletteSpin"
        :isShowYourWin="isShowYourWin"
        :isShowYourWinShow="isShowYourWinShow"
        @spin-play="spinPlay"
      />    
      <Parallax v-if="isMobileL" />
      <div
        v-else
        class="-translate-y-7 z-10"
      >
        <img src="./assets/images/mobile-elements.png" alt="mobile elements">
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>

.roulette-center {

  &:before {
    content: "";
    display: flex;
    flex: 1 1 0%;
  }
}

</style>
