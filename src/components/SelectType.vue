<script setup>
defineProps({
  currentRoundNumber: Number,
});

const emit = defineEmits(['onChangePhase']);
</script>

<template>
  <div class="w-[200%] h-4 absolute -rotate-[26.5deg] bg-slate-50 border-slate-900 border-4"></div>
  <div class="flex flex-col w-screen h-screen relative">
    <div class="flex-1 flex items-end relative">
      <div class="slide-in-tl option bg-amber-500 border-amber-700 absolute left-[calc(100vw/10)]" @click="emit('onChangePhase', 'question', currentRoundNumber + 1)">QUESTION</div>
    </div>
    <div class="flex-1 flex items-center justify-center">
      <div
        class="text-5xl w-[200px] h-[200px] flex items-center justify-center font-bold border-4 bg-slate-50 rounded-full border-slate-900 text-slate- 900">
        or</div>
    </div>
    <div class="flex-1 flex items-start relative">
      <div class="slide-in-br option bg-red-500 border-red-700 absolute right-[calc(100vw/10)]" @click="emit('onChangePhase', 'challenge', currentRoundNumber + 1)">CHALLENGE</div>
    </div>
  </div>
</template>

<style scoped>
.option {
  @apply text-5xl font-bold px-12 py-8 rounded-3xl text-slate-50 border-4 w-[400px] text-center cursor-pointer;
}

.slide-in-tl {
  -webkit-animation: slide-in-tl 0.5s cubic-bezier(0.250, 0.460, 0.450, 0.940) 0.5s both;
          animation: slide-in-tl 0.5s cubic-bezier(0.250, 0.460, 0.450, 0.940) 0.5s both;
}
@keyframes slide-in-tl {
  0% {
    -webkit-transform: translateY(-1000px) translateX(-1000px);
            transform: translateY(-1000px) translateX(-1000px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateY(0) translateX(0);
            transform: translateY(0) translateX(0);
    opacity: 1;
  }
}

.slide-in-br {
  -webkit-animation: slide-in-br 0.5s cubic-bezier(0.250, 0.460, 0.450, 0.940) 1s both;
          animation: slide-in-br 0.5s cubic-bezier(0.250, 0.460, 0.450, 0.940) 1s both;
}
@keyframes slide-in-br {
  0% {
    -webkit-transform: translateY(1000px) translateX(1000px);
            transform: translateY(1000px) translateX(1000px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateY(0) translateX(0);
            transform: translateY(0) translateX(0);
    opacity: 1;
  }
}

</style>
