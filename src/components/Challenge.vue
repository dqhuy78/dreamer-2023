<script setup>
defineProps({
  challengeNumber: Number,
  challenge: String,
})
</script>

<template>
  <h2 id="game-round-ttl" class="text-7xl font-black mb-6 text-amber-500 -mt-10">
      CHALLENGE {{ challengeNumber }}
    </h2>
    <div id="game-card" class="relative h-[350px] w-[770px] rounded-3xl px-10 pt-3">
      <div class="z-1 absolute left-0 top-0 h-[350px] w-[770px] -rotate-3 rounded-3xl bg-red-500 shadow-bgr"></div>
      <div class="z-1 absolute left-0 top-0 h-[350px] w-[770px] rounded-3xl bg-slate-50"></div>
      <div class="isolate z-10">
        <div id="game-question" class="mb-16">
          <h3 class="my-6 select-none text-4xl leading-snug font-semibold text-slate-900 text-center">
            {{ challenge }}
          </h3>
        </div>
        <div id="game-answer" class="flex items-center justify-around">
          <div
            class="flex w-[250px] cursor-pointer select-none items-center rounded-3xl border-4 p-7 text-2xl transition-all justify-center font-bold text-slate-900 border-green-700 hover:bg-green-500 hover:text-slate-50">
            CHƠI LUÔN
          </div>
          <div class="group relative cursor-pointer py-2">
            <div
              class="invisible left-[50%] translate-x-[-50%] translate-y-0 absolute top-[-35%] text-xl group-hover:visible w-max text-amber-500 bg-amber-500 px-2 py-1 rounded-lg">
              <p class="text-slate-50">Xin lỗi bạn không thể từ chối</p>
              <svg class="absolute left-[50%] translate-x-[-50%] translate-y-0 z-10 -bottom-1" width="8" height="4"
                viewBox="0 0 16 10" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M8 10L0 0L16 1.41326e-06L8 10Z" fill="currentColor" />
              </svg>
            </div>
            <div
              class="flex w-[250px] cursor-not-allowed select-none items-center rounded-3xl border-4 p-7 text-2xl transition-all justify-center font-bold text-slate-900 border-red-700 hover:bg-red-500 hover:text-slate-50">
              TỪ CHỐI
            </div>
          </div>
        </div>
      </div>
    </div>
</template>
