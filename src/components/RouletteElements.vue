<script setup lang="ts">
import { computed } from 'vue';
import type { IRouletteSpin, ISpinCount } from '../types/types';
import RouletteItem from './RouletteItem.vue';
import rouletteItemsData  from '../data/data.json';

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
    class="roulette relative max-w-[450px] max-h-[450px] w-[50vmax] h-[50vmax] m-auto  text-center rounded-full select-none overflow-hidden mobile-l:max-w-[300px] mobile-l:max-h-[300px] z-[9]"
  >
    <RouletteItem 
      v-for="(rouletteItem, index) in rouletteItemsData"
      :title="rouletteItem.title"
      :subtitle="rouletteItem.subtitle"
      :index="index"
    />
  </div>
</template>

<style lang="scss" scoped>
.roulette__elements {

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
