<script setup>
const emit = defineEmits(['onChangePhase']);
</script>

<template>
  <div>
    <h2 class="game-welcome-msg mb-4 font-semibold text-slate-50 w-[1200px] h-[120px] text-[40px]" style="line-height: 1.4">
    </h2>
  </div>
  <div class="w-[500px] flex items-center justify-between">
    <button
      class="roll-in-left text-4xl font-bold w-[200px] border-4 rounded-3xl p-7 border-green-700 bg-green-500 text-slate-50"
      @click="emit('onChangePhase')"
    >
      YES
    </button>
    <button
      class="roll-in-right text-4xl font-bold w-[200px] border-4 rounded-3xl p-7 border-red-700 bg-red-500 text-slate-50 group-hover:block group"
      @click="emit('onChangePhase')"
    >
      <span class="hidden group-hover:block">YES</span>
      <span class="group-hover:hidden">NO</span>
    </button>
  </div>
</template>

<style lang="scss" scoped>
@import '@/assets/typed.scss';
@import '@/assets/typing.scss';

.roll-in-left {
  -webkit-animation: roll-in-left 0.6s ease-out 9s both;
  animation: roll-in-left 0.6s ease-out 9s both;
}

@-webkit-keyframes roll-in-left {
  0% {
    -webkit-transform: translateX(-800px) rotate(-540deg);
    transform: translateX(-800px) rotate(-540deg);
    opacity: 0;
  }

  100% {
    -webkit-transform: translateX(0) rotate(0deg);
    transform: translateX(0) rotate(0deg);
    opacity: 1;
  }
}

@keyframes roll-in-left {
  0% {
    -webkit-transform: translateX(-800px) rotate(-540deg);
    transform: translateX(-800px) rotate(-540deg);
    opacity: 0;
  }

  100% {
    -webkit-transform: translateX(0) rotate(0deg);
    transform: translateX(0) rotate(0deg);
    opacity: 1;
  }
}

.roll-in-right {
  -webkit-animation: roll-in-right 0.6s ease-out 9s both;
  animation: roll-in-right 0.6s ease-out 9s both;
}

@-webkit-keyframes roll-in-right {
  0% {
    -webkit-transform: translateX(800px) rotate(540deg);
    transform: translateX(800px) rotate(540deg);
    opacity: 0;
  }

  100% {
    -webkit-transform: translateX(0) rotate(0deg);
    transform: translateX(0) rotate(0deg);
    opacity: 1;
  }
}

@keyframes roll-in-right {
  0% {
    -webkit-transform: translateX(800px) rotate(540deg);
    transform: translateX(800px) rotate(540deg);
    opacity: 0;
  }

  100% {
    -webkit-transform: translateX(0) rotate(0deg);
    transform: translateX(0) rotate(0deg);
    opacity: 1;
  }
}
</style>
