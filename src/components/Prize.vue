<script setup lang="ts">
import { type ISpinCount } from '../types/types';

const props = defineProps<ISpinCount>();

</script>
<template>
  <div class="relative flex-1 flex items-center gap-5 mb-5 z-10 tablet:flex-col tablet:order-1 tablet:mb-0 mobile-l:gap-3 mobile-l:mb-0">
      <div 
        class="prize relative origin-center w-[188px] h-[142px] z-[10] mobile-l:w-[140px] mobile-l:h-[105px]"
        :class="props.spinCount < 2 && 'prize__win'"
      >
        <div class="prize__front absolute top-0 left-0 w-full h-full">
          <img
            src="@/assets/images/prize.svg"
            alt="prize"
          >
        </div>
        <div class="prize__back absolute top-0 left-0 flex w-full h-full">
          <img
            class="absolute top-0 left-0 flex w-full h-full"
            src="@/assets/images/prize-win.svg"
            alt="prize"
          >
          <div class="m-auto text-center rotate-y-180 z-10">
            <p class="text-lg font-bold leading-[1.24] mobile-l:text-sm">150 ФС</p>
          </div>
        </div>
      </div>
      <div 
        class="prize relative origin-center w-[188px] h-[142px] z-[10] mobile-l:w-[140px] mobile-l:h-[105px]"
        :class="props.spinCount === 0 && 'prize__win'"
      >
        <div class="prize__front absolute top-0 left-0 w-full h-full">
          <img
            src="@/assets/images/prize.svg"
            alt="prize"
          >
        </div>
        <div class="prize__back absolute top-0 left-0 flex w-full h-full">
          <img
            class="absolute top-0 left-0 flex w-full h-full"
            src="@/assets/images/prize-win.svg"
            alt="prize"
          >
          <div class="m-auto text-center rotate-y-180 z-10">
            <p class="text-lg font-bold leading-[1.24] mobile-l:text-sm">+225%</p>
            <p class="text-xs">на депозит</p>
          </div>
        </div>
      </div>
    </div>
</template>

<style lang="scss" scoped>
.prize {
  perspective: 188px;
  transform-style: preserve-3d;
  transition: transform 500ms linear;
  will-change: transform;

  &__win {
    transform: rotateY(180deg);
  }

  &__front {
    backface-visibility: hidden;
    transform: rotateY(0deg);
    z-index: 2;
  }

  &__back {
    transform: rotateY(0deg);

    div {
      transform: rotateY(180deg);
    }
  }
}
</style>
