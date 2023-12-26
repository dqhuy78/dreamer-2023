<script setup>
import { nextTick, ref } from 'vue';

import Welcome from './components/Welcome.vue';
import Question from './components/Question.vue';
import Challenge from './components/Challenge.vue';
import Prize from './components/Prize.vue';
import SelectType from './components/SelectType.vue';
import Final from './components/Final.vue';

const questions = [
  {
    content: 'Con ma lo choi nhảy ở giữa màu cam là ai?',
    imageSrc: 'https://images.viblo.asia/612e9ecf-c7b5-4e7a-b8bf-ff983f9308a4.jpg',
    answers: ['Ước Mơ', 'Lê Mến', 'Quỳnh Mai'],
    correctAnswerIndex: 2,
  },
  {
    content: 'Vào sinh nhật của Lê Mến, chúng ta đã chiêu đãi Lê Mến món ăn nào?',
    imageSrc: 'https://images.viblo.asia/3f8a7a86-8ec8-499a-bf8b-32568237d42a.jpg',
    answers: ['Canh trứng', 'Lẩu nấm', 'Buffet'],
    correctAnswerIndex: 2,
  },
  {
    content: 'Trong năm 2023, Hải Nam đã chuyển nhà bao nhiều lần?',
    imageSrc: 'https://images.viblo.asia/a953128f-374e-47a6-93d9-36530ba22b3d.jpg',
    answers: ['1 lần', '2 lần', '3 lần'],
    correctAnswerIndex: 1,
  },
  {
    content: 'Kênh tiktok của Idol Nghiêm Nhung tên là gì?',
    imageSrc: 'https://images.viblo.asia/f9f5e004-44a1-418e-92a4-a858e7d92d60.png',
    answers: ['Nghiemnhung912', 'Nghiemnhung911', 'Nghiemnhung811'],
    reduceAnswerSize: true,
    correctAnswerIndex: 0,
  },
  {
    content: 'Vân Hạnh đã đi bao nhiêu nước?',
    imageSrc: 'https://images.viblo.asia/c3380add-7707-46d0-ac75-d51d46f63680.jpg',
    answers: ['5', '8', '10'],
    correctAnswerIndex: [0, 1, 2],
  }
];

const challenges = [
  'Hãy trải qua một ngày và không mắng bất cứ ai cả!',
  'Hãy mặc một 1 chiếc áo/váy màu hồng vào ngày mai!',
  'Mời 1 Line bất kì trong HRV món thịt xiên nướng!',
  'Hãy thể hiện tình cảm yêu quý với 5 member HRV bất kì!',
  'Hãy cảm ơn 5 members bất kì trong HRV!',
];

const prizes = [
  {
    content: 'Hãy mở ngăn kéo bàn thứ 2 và khám phá món quà đầu tiên nhé.',
  },
  {
    content: 'Một bữa trưa với chúng tôi vào trưa thứ 3 (26/12).',
  },
  {
    content: 'Bạn sẽ được gặp chồng/vợ và con chúng tôi. Chúc cho buổi gặp mặt này sẽ tiếp thêm động lực sản xuất baby cho bạn.',
    reduceSize: true,
  },
  {
    content: 'Chúng ta sẽ cùng nhau làm từ thiện. Hy vọng rằng những điều nhỏ bé chúng mình làm nhau sẽ mang lại chút ấm áp cho những người cần giúp đỡ.',
    reduceSize: true,
  },
  {
    content: 'Bạn đã có được chúng tôi',
  }
];

const phase = ref('welcome');
const roundNumber = ref(-1);
const prizeTitle = ref();

const onChangePhase = (newPhase, newRoundNumber = undefined) => {
  if (newRoundNumber !== undefined) {
    roundNumber.value = newRoundNumber;
  }
  nextTick(() => {
    phase.value = newPhase;
  });
}

const onChooseAnswer = (isCorrect) => {
  setTimeout(() => {
    if (isCorrect) {
      onChangePhase('prize');
    } else {
      onChangePhase('prize');
      prizeTitle.value = 'Phần Quà An Ủi'

    }
  }, 2000);
}

const onAcceptChallenge = () => {
  setTimeout(() => {
    onChangePhase('prize');
  }, 200);
}
</script>

<template>
  <div class="game-bgr">

    <Welcome v-if="phase === 'welcome'" @onChangePhase="onChangePhase('select')"/>
    <SelectType v-else-if="phase === 'select'" :currentRoundNumber="roundNumber" @onChangePhase="onChangePhase" />
    <Question
      v-else-if="phase === 'question'"
      :roundNumber="roundNumber"
      :question="questions[roundNumber].content"
      :imageSrc="questions[roundNumber].imageSrc"
      :answers="questions[roundNumber].answers"
      :reduceAnswerSize="questions[roundNumber].reduceAnswerSize"
      :correctAnswerIndex="questions[roundNumber].correctAnswerIndex"
      @onChooseAnswer="onChooseAnswer" />
    <Challenge
      v-else-if="phase === 'challenge'"
      :challengeNumber="roundNumber"
      @onAcceptChallenge="onAcceptChallenge"
      :challenge="challenges[roundNumber]" />
    <Prize v-else-if="phase === 'prize'"
      :title="prizeTitle"
      :prizeName="prizes[roundNumber].content"
      :reduceSize="prizes[roundNumber].reduceSize"
      :currentRoundNumber="roundNumber"
      @onChangePhase="() => {
        if (roundNumber === 4) return onChangePhase('final');
        onChangePhase('select');
        prizeTitle = undefined;
      }" />
      <Final v-else-if="phase === 'final'"/>
  </div>
</template>
