<script setup lang="ts">
import { computed } from 'vue';
import type { IRouletteSpin, ISpinCount } from '../types/types';

const props = defineProps<IRouletteSpin & ISpinCount>()

// Количеств оборотов колеса 
const spinDefault = 3 * 360;

// Градус оборота для первого и второго приза
const testFirst = 180;
const testSecond = 315;

// Для добавлении класа анимаци врашения
const animationClasses = computed(() => {  
  return props.rouletteSpin ? 'roulette__elements_spining' : 'roulette__elements_forwards';
})

// Для анимации врашения
const spinRotate = computed(() => {
  return props.spinCount === 2 ? `${spinDefault + testFirst}deg` : `${spinDefault + testSecond}deg`;
})

// Последная позицыя выграша
const forwardsRotate = computed(() => {
  return props.spinCount === 1 ? `${testFirst}deg` : props.spinCount === 0 && `${testSecond}deg`;
})

</script>

<template>
  <div
    :class="animationClasses"
    class="roulette__elements relative grid grid-rows-roulette grid-cols-roulette max-w-[450px] max-h-[450px] w-full h-full m-auto text-white rounded-[50%] z-[3] mobile-l:max-w-[300px] mobile-l:max-h-[300px]"
  >
    <div class="row-start-2 row-end-6 col-start-2 col-end-6 flex">
      <div class="mx-auto pt-10 px-5 text-center rotate-[-45deg] select-none mobile-l:pt-7">
        <p class="text-lg font-bold leading-[1.24] mobile-l:text-xs">+450%</p>
        <p class="text-xs mobile-l:text-[8px]">на депозит</p>
      </div>
    </div>
    <div class="row-start-1 row-end-5 col-start-5 col-end-9 flex">
      <div class="mt-8 mx-auto px-[20px] text-center select-none mobile-l:mt-6">
        <p class="text-lg leading-[1.24] mobile-l:text-xs">Без выигрыша</p>
      </div>
    </div>
    <div class="row-start-2 row-end-6 col-start-8 col-end-12 flex">
      <div class="mx-auto pt-10 px-5 text-center rotate-45 select-none mobile-l:pt-7">
        <p class="text-lg font-bold leading-[1.24] mobile-l:text-xs">+225%</p>
        <p class="text-xs mobile-l:text-[8px]">на депозит</p>
      </div>
    </div>
    <div class="row-start-5 row-end-9 col-start-1 col-end-6 flex">
      <div class="mx-auto pt-5 text-center rotate-[-90deg] select-none mobile-l:pt-3">
        <p class="text-lg font-bold leading-[1.24] mobile-l:text-xs">+225%</p>
        <p class="text-xs mobile-l:text-[8px]">на депозит</p>
      </div>
    </div>
    <div class="row-start-5 row-end-9 col-start-8 col-end-13 flex">
      <div class="mx-auto pt-4 text-center rotate-90 select-none mobile-l:pt-3">
        <p class="text-lg font-bold mobile-l:text-xs">100 ФС</p>
      </div>
    </div>
    <div class="row-start-8 row-end-12 col-start-2 col-end-6 flex">
      <div class="mx-auto pt-10 px-5 text-center rotate-[-135deg] select-none mobile-l:pt-6">
        <p class="text-lg leading-[1.24] mobile-l:text-xs">Без выигрыша</p>
      </div>
    </div>
    <div class="row-start-9 row-end-13 col-start-5 col-end-9 flex">
      <div class="mx-auto pt-6 text-center rotate-[180deg] select-none mobile-l:pt-5">
        <p class="text-lg font-bold mobile-l:text-xs">150 ФС</p>
      </div>
    </div>
    <div class="row-start-8 row-end-12 col-start-8 col-end-12 flex">
      <div class="mx-auto pt-10 text-center rotate-[135deg] select-none mobile-l:pt-6">
        <p class="text-lg font-bold leading-[1.24] mobile-l:text-xs">150%</p>
        <p class="text-xs mobile-l:text-[8px]">на депозит</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>

.roulette__elements {
    background: url('../assets/images/roulette/main-wheal.webp') center/contain no-repeat;
    z-index: 9;

    &_spining {
      animation: rotate-spin 5s cubic-bezier(0, -0.02, 0, 1.01) forwards;
    }

    &_forwards {
      transform: rotate(v-bind(forwardsRotate));
    }
}

@keyframes rotate-spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(v-bind(spinRotate));
  }
}

</style>
1