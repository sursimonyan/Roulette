<script setup lang="ts">
import type { IRouletteItem } from '@/types/types';
import { computed } from 'vue';

const props = defineProps<IRouletteItem>();

const darkOrLight = computed(() => {
  return props.index % 2 === 0 || props.index === 0 ? 'url(/src/assets/images/roulette/sector-light.png)' : 'url(/src/assets/images/roulette/sector-dark.png)';
})

const rotateDeg = computed(() => {
  if ((props.index * 45) < 135) {
    return `rotate-${props.index * 45}`;
  }

  return `rotate-[${props.index * 45}deg]`;
})

</script>

<template>
  <div
    class="rouletteitem absolute left-1/2 flex justify-center max-w-[210px] max-h-[238px] w-1/2 h-1/2 pt-8 px-3 text-xl text-white -translate-x-1/2 origin-bottom text-cebter mobile-l:pt-5"
    :class="rotateDeg"
  >
    <div class="px-8 select-none">
      <p class="text-lg leading-[1.24] mobile-l:text-xs">{{ props.title }}</p>
      <p 
        v-if="props.subtitle"
        class="text-xs mobile-l:text-[8px]"
      >{{ props.subtitle }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>

.rouletteitem {
  clip-path: polygon(100% 0, 50% 100%, 0 0);
  background: v-bind(darkOrLight) center/contain no-repeat;
}

</style>
