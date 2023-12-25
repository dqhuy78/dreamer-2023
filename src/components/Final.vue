<template>
  <div class="w-screen h-screen overflow-hidden bg-slate-900/35 flex items-center p-6 flex-col">
    <p class="final-word text-[34px] leading-[1.4] font-semibold w-[1200px] h-[250px]"></p>
    <img src="../assets/final.png" class="w-[calc(100vh)] h-auto mt-4 hover:!scale-150 hover:-mt-20 transition-all select-none" />
  </div>
</template>

<style lang="scss" scoped>
@import '@/assets/typed.scss';
.final-word {
  color: theme('colors.slate.50');
  @include typed('Chúc Ước Mơ có 1 ngày sinh nhật thật ấm áp và đầy ý nghĩa.\A 1 năm qua đi bạn đã làm rất tổi rồi, cảm ơn bạn vì đã không ngừng cố gắng.\A Dù vui buồn hay mệt mỏi, hãy nhớ rằng:\A Ai cũng cần Ước Mơ và Ước Mơ cần tất cả mọi người.\A We all love you', null, (iterations: 0, caret-width: 6px));
}
</style>
