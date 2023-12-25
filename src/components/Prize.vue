<script setup>
defineProps({
  prizeName: String,
  reduceSize: Boolean,
  currentRoundNumber: Number,
  title: String,
});

const emit = defineEmits(['onChangePhase']);
</script>

<template>
  <div class="absolute bg-slate-900/40 w-screen h-screen left-0 top-0">
  </div>
  <h3 :class="`game-prize-ttl text-5xl -mt-8 mb-6 font-black text-slate-50 z-20 ${title ? 'stroke-red-500' : 'stroke-amber-500'}`">
    {{ title ? title : 'Chúc Mừng Bạn' }}
  </h3>
  <img class="z-10 w-[500px] h-auto scale-in-bottom absolute"
    src="../assets/gift.png" />
  <div
    class="z-20 w-[600px] h-[350px] bg-slate-50 rounded-3xl flex items-center justify-center flex-col px-12 overflow-hidden relative border-amber-500 border-4 flip-in-hor-bottom">
    <div class="w-[100px] h-[40px] bg-amber-500 -rotate-45 absolute top-0 left-20"></div>
    <div class="w-[120px] h-[40px] bg-amber-500 -rotate-45 absolute top-28 -left-12"></div>
    <img src="../assets/bow.png"
      class="absolute left-2 top-2 -rotate-45 w-[150px]" />
    <p class="leading-snug font-semibold pl-20"
      :class="`${reduceSize ? 'text-2xl' : 'text-3xl'}`"
    >
      {{ prizeName }}
    </p>
    <div class="w-[600px] h-[40px] bg-amber-500 -rotate-45 absolute -bottom-10 -right-40"></div>
  </div>
  <p class="w-[590px] mt-4 z-20 flex justify-end text-slate-50 font-semibold">
    <span
      class="text-2xl py-2 px-4 rounded-3xl bg-amber-500 cursor-pointer flex items-center w-fit gap-1 appear-and-shake"
      @click="emit('onChangePhase')"
    >
      Tiếp tục
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-7 h-7">
        <path
          d="M5.055 7.06C3.805 6.347 2.25 7.25 2.25 8.69v8.122c0 1.44 1.555 2.343 2.805 1.628L12 14.471v2.34c0 1.44 1.555 2.343 2.805 1.628l7.108-4.061c1.26-.72 1.26-2.536 0-3.256l-7.108-4.061C13.555 6.346 12 7.249 12 8.689v2.34L5.055 7.061Z" />
      </svg>
    </span>
  </p>
</template>

<style scoped>
.game-prize-ttl {
  -webkit-text-stroke: 2px theme('colors.amber.500');
}
</style>
