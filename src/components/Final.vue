<template>
  <div class="w-screen h-screen overflow-hidden bg-slate-900/35 flex items-center p-6 flex-col">
    <p class="final-word text-[34px] leading-[1.4] font-semibold w-[1200px] h-[270px]"></p>
    <p class="text-[34px] leading-[1.4] font-semibold w-[1200px] text-right text-slate-50 my-2 slide-in-right">- From
      Leader Team with Love -</p>
    <img src="../assets/final.png" class="w-[calc(95vh)] h-auto mt-4 transition-all select-none swing-in-bottom-fwd" />
  </div>
</template>

<style lang="scss" scoped>
@import '@/assets/typed.scss';

.final-word {
  color: theme('colors.slate.50');
  @include typed('Chúc Ước Mơ có 1 ngày sinh nhật ấm áp và đầy ý nghĩa.\A 1 năm qua đi bạn đã làm rất tốt rồi, cảm ơn bạn vì đã không ngừng cố gắng.\A Dù vui buồn hay mệt mỏi, hãy nhớ rằng:\A Ai cũng cần Ước Mơ, và Ước Mơ có tất cả mọi người.\A Gửi  1000 trái tim yêu thương đến người Manager dũng cảm.', null, (iterations: 0, caret-width: 6px));
}

.slide-in-right {
  -webkit-animation: slide-in-right 0.5s cubic-bezier(0.250, 0.460, 0.450, 0.940) 39s both;
  animation: slide-in-right 0.5s cubic-bezier(0.250, 0.460, 0.450, 0.940) 29s both;
}

@keyframes slide-in-right {
  0% {
    -webkit-transform: translateX(1000px);
    transform: translateX(1000px);
    opacity: 0;
  }

  100% {
    -webkit-transform: translateX(0);
    transform: translateX(0);
    opacity: 1;
  }
}

.swing-in-bottom-fwd {
  -webkit-animation: swing-in-bottom-fwd 0.5s cubic-bezier(0.175, 0.885, 0.320, 1.275) 29.5s both;
  animation: swing-in-bottom-fwd 0.5s cubic-bezier(0.175, 0.885, 0.320, 1.275) 29.5s both;
}

@keyframes swing-in-bottom-fwd {
  0% {
    -webkit-transform: rotateX(100deg);
    transform: rotateX(100deg);
    -webkit-transform-origin: bottom;
    transform-origin: bottom;
    opacity: 0;
  }

  100% {
    -webkit-transform: rotateX(0);
    transform: rotateX(0);
    -webkit-transform-origin: bottom;
    transform-origin: bottom;
    opacity: 1;
  }
}
</style>
