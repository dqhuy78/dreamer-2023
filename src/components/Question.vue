<script setup>
import { ref } from 'vue';

const props = defineProps({
  roundNumber: Number,
  question: String,
  imageSrc: String,
  answers: Array,
  reduceAnswerSize: Boolean,
  correctAnswerIndex: Number || Array,
});

const emit = defineEmits(['onChooseAnswer']);

const startLetter = ['A', 'B', 'C'];
const answerClass = ref(['', '', '']);
const disableClick = ref(false);
const onPickAnswer = (index) => {
  if (disableClick.value) return;
  if (typeof props.correctAnswerIndex === 'number') {
    if (index === props.correctAnswerIndex) {
      answerClass.value[index] = 'game-correct-answer';
      emit('onChooseAnswer', true);
    } else {
      answerClass.value[index] = 'game-wrong-answer';
      emit('onChooseAnswer', false);
    }
  } else {
    if (props.correctAnswerIndex.includes(index)) {
      answerClass.value[index] = 'game-correct-answer';
      emit('onChooseAnswer', true);
    } else {
      answerClass.value[index] = 'game-wrong-answer';
      emit('onChooseAnswer', false);
    }
  }
  disableClick.value = true;
}
</script>

<template>
  <h2 id="game-round-ttl" class="text-7xl font-black mb-6 text-amber-500 -mt-10">
    ROUND {{ roundNumber + 1 }}
  </h2>
  <div id="game-card" class="relative h-[550px] w-[900px] rounded-3xl px-10 pt-3">
    <div class="z-1 absolute left-0 top-0 h-[550px] w-[900px] -rotate-3 rounded-3xl bg-amber-300 shadow-bgr"></div>
    <div class="z-1 absolute left-0 top-0 h-[550px] w-[900px] rounded-3xl bg-slate-50"></div>
    <div class="isolate z-10">
      <div id="game-question" class="mb-16">
        <h3 class="my-6 select-none text-2xl font-semibold text-slate-900">
          {{ question }}
        </h3>
        <div class="flex w-full select-none items-center justify-center">
          <img :src="imageSrc" class="h-auto w-[300px] rounded-xl hover:scale-[200%] transition-all" />
        </div>
      </div>
      <div id="game-answer" class="flex items-center justify-between">
        <div v-for="(answer, index) in answers"
          class="flex w-[250px] cursor-pointer select-none items-center rounded-3xl border-4 border-amber-500 p-7 text-slate-900 transition-all hover:bg-amber-300"
            :class="`${reduceAnswerSize ? 'text-xl' : 'text-2xl'} ${answerClass[index]}`
            "
            @click="onPickAnswer(index)"
          >
          <p class="mr-3 flex items-center justify-center font-bold">{{ startLetter[index] }}.</p>
          <p class="font-bold">{{ answer }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.game-correct-answer {
  @apply border-green-700 bg-green-500 text-slate-50 animate-pulse;

  &:hover {
    @apply !bg-green-500;
  }
}

.game-wrong-answer {
  @apply border-red-700 bg-red-500 text-slate-50;

  &:hover {
    @apply !bg-red-500;
  }
}
</style>
