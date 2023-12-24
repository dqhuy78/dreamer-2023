<script setup>
import Welcome from './components/Welcome.vue';
import Question from './components/Question.vue';
import Challenge from './components/Challenge.vue';
import Prize from './components/Prize.vue';
import { ref } from 'vue';

const questions = [
  {
    content: 'Con mai lo choi nhảy ở giữa màu cam là ai?',
    imageSrc: 'https://learn.viblo.asia/uploads/6/4/643ca156-1c12-4291-89fa-8daf5a9d52ac.jpg',
    answers: ['Ước Mơ', 'Lê Mến', 'Quỳnh Mai'],
  },
  {
    content: 'Vào sinh nhật của Lê Mến, chúng ta đã chiêu đãi Lê Mến món ăn nào?',
    imageSrc: 'https://learn.viblo.asia/uploads/6/4/643ca156-1c12-4291-89fa-8daf5a9d52ac.jpg',
    answers: ['Canh trứng', 'Lẩu nấm', 'Buffet'],
  },
  {
    content: 'Trong năm 2023, Hải Nam đã chuyển nhà bao nhiều lần?',
    imageSrc: 'https://learn.viblo.asia/uploads/6/4/643ca156-1c12-4291-89fa-8daf5a9d52ac.jpg',
    answers: ['1 lần', '2 lần', '3 lần'],
  },
  {
    content: 'Kênh tiktok của Idol Nghiêm Nhung tên là gì?',
    imageSrc: 'https://learn.viblo.asia/uploads/6/4/643ca156-1c12-4291-89fa-8daf5a9d52ac.jpg',
    answers: ['Nghiemnhung912', 'Nghiemnhung911', 'Nghiemnhung811'],
    reduceAnswerSize: true,
  },
  {
    content: 'Vân Hạnh đã đi bao nhiêu nước?',
    imageSrc: 'https://learn.viblo.asia/uploads/6/4/643ca156-1c12-4291-89fa-8daf5a9d52ac.jpg',
    answers: ['5', '8', '10'],
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
    content: 'Hãy mở ngăn kéo bàn thứ 2 và khám phá mòn quà đầu tiên nhé.',
  },
  {
    content: 'Một bữa trưa với chúng tôi vào thứ 4 (27/12). Thời gian sẽ gửi đến bạn sớm khi trò chơi kết thúc.',
  },
  {
    content: 'Bạn sẽ được gặp chồng/vờ và con chúng tôi. Chúc cho buổi gặp mặt này sẽ tiếp thêm động lực sản xuất baby cho bạn.',
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
const roundNumber = ref(0);
const roundContent = ref('');
</script>

<template>
  <div class="game-bgr">
    <Welcome />
  </div>
  <hr class="my-4 bg-amber-500" />
  <div class="game-bgr" v-for="(question, index) in questions">
    <Question
      :roundNumber="index"
      :question="question.content"
      :imageSrc="question.imageSrc"
      :answers="question.answers"
      :reduceAnswerSize="question.reduceAnswerSize" />
  </div>
  <hr class="my-4 bg-amber-500" />
  <div class="game-bgr" v-for="(challenge, index) in challenges">
    <Challenge
      :challengeNumber="index + 1"
      :challenge="challenge" />
  </div>
  <hr class="my-4 bg-amber-500" />
  <div class="game-bgr relative" v-for="prize in prizes">
    <Prize :prizeName="prize.content" :reduceSize="prize.reduceSize" />
  </div>
</template>


