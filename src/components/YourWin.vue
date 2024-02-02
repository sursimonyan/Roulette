<template>
  <div
    class="yourwin absolute top-[42px] left-[42px] flex flex-col max-w-[450px] max-h-[450px] w-full h-full m-auto rounded-full overflow-hidden z-30 mobile-l:max-w-[300px] mobile-l:max-h-[300px] mobile-l:top-[13px] mobile-l:left-[13px]">
    <div class="pt-[50px] font-bold text-center z-10 mobile-l:pt-[26px]">
      <p class="mb-3 text-lg">Ваш выигрыш</p>
      <p class="text-[40px] text-[#F9D193] leading-[1.3] mobile-l:text-[26px]">150 ФС +225%</p>
      <p class="mb-7 leading-[1.24] mobile-l:mb-4">на депозит</p>
      <button class="relative h-12 px-6 text-sm bg-[#CE2951] rounded-3xl z-[2] hover:bg-[#D72F58] mobile-l:h-10">Забрать приз</button>
      <div class="absolute bottom-0 left-0">
        <img src="../assets/images/yourwin/yourwin-gift.png" alt="your win gift">
      </div>
    </div>
    <div class="absolute -bottom-[30%] left-0">
      <img class="yourwin__start_front absolute z-[3]" src="../assets/images/yourwin/yourwin-animation-star-front.svg" alt="star ligth front">
      <img class="yourwin__start_back" src="../assets/images/yourwin/yourwin-animation-star-back.svg" alt="star ligth back">
    </div>
  </div>
</template>

<style lang="scss" scoped>
.yourwin {
  background: url('@/assets/images/yourwin/yourwin-bg.png') center no-repeat;

  &__start_front {
    animation: start-rotating 15s linear infinite;  
  }

  &__start_back {
    animation: start-rotating 20s linear infinite;  
  }
}

@keyframes start-rotating {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(-360deg);
  }
}
</style>
