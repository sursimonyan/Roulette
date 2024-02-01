<template>
  <button class="relative m-auto z-10 hover:brightness-110">
    <span class="absolute top-12 left-[49px] text-2xl font-bold mobile-l:text-base mobile-l:top-[31px] mobile-l:left-[34px]">
      <slot></slot>
    </span>
    <img class="mobile-l:w-[76px]" src="@/assets/images/roulette/spin.png" alt="spin">
  </button>
</template>
