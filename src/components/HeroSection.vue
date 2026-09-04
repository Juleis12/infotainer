<template>
  <header class="relative isolate overflow-hidden border-b border-[#ead5d2] bg-[#fff8f4] text-[#34181d] dark:border-[#42232a] dark:bg-[#1d0b10]">
    <img src="../assets/bg3.jpg" alt="" class="absolute inset-0 -z-20 h-full w-full object-cover opacity-15 mix-blend-multiply dark:opacity-10" />
    <div class="absolute inset-0 -z-10 bg-[radial-gradient(circle_at_82%_42%,rgba(194,45,65,0.30),transparent_30%),linear-gradient(112deg,#fff8f4_0%,#fff4ee_48%,#ead1d0_100%)] dark:bg-[radial-gradient(circle_at_82%_42%,rgba(194,45,65,0.34),transparent_30%),linear-gradient(112deg,#1d0b10_0%,#2a0f16_52%,#4b1824_100%)]"></div>
    <div class="mx-auto grid max-w-7xl items-center gap-10 px-4 py-16 sm:px-6 sm:py-24 lg:grid-cols-[1.05fr_0.95fr] lg:px-8 lg:py-28">
      <div class="max-w-3xl">
        <p class="text-xs font-black uppercase tracking-[0.3em] text-[#a82135] dark:text-[#ef777d]">Learn · Explore · Grow</p>
        <h1 class="mt-5 text-5xl font-black leading-[0.96] tracking-[-0.045em] sm:text-6xl lg:text-7xl">
          The Best<br /><span class="text-[#9e2036] dark:text-[#f06a76]">Educational Channels</span>
        </h1>
        <p class="mt-6 max-w-2xl text-lg leading-8 text-[#61494b] dark:text-[#d9c1c3] sm:text-xl">
          A curated directory of YouTube channels that <strong>inform, inspire</strong> and entertain. Discover quality content on science, technology, history and more.
        </p>
        <div class="mt-8 flex flex-wrap gap-3">
          <a href="#get-started" class="inline-flex items-center rounded-xl bg-[#b51f39] px-6 py-3 text-sm font-black text-white shadow-lg shadow-[#761326]/20 transition hover:-translate-y-0.5 hover:bg-[#c72d48] focus:outline-none focus:ring-2 focus:ring-[#e35d6c] focus:ring-offset-2 focus:ring-offset-[#fff8f4] dark:focus:ring-offset-[#1d0b10]">▶ <span class="ml-2">Explore Channels</span><span class="ml-3">→</span></a>
          <a href="#topics" class="inline-flex items-center rounded-xl border border-[#c98e94] bg-white/70 px-6 py-3 text-sm font-black text-[#7e2333] transition hover:bg-white dark:border-[#70404a] dark:bg-white/5 dark:text-[#f0b2b7]">▦ <span class="ml-2">Browse Topics</span></a>
        </div>
      </div>
      <div class="relative hidden min-h-[320px] items-center justify-center lg:flex">
        <div class="absolute h-72 w-72 rounded-full bg-[#b51f39]/15 blur-3xl"></div>
        <div class="relative grid h-64 w-80 place-items-center rounded-[2rem] border border-[#b51f39]/25 bg-gradient-to-br from-[#5e1020] to-[#a91e38] shadow-2xl shadow-[#5b0f1e]/25 rotate-[-3deg]">
          <div class="grid h-28 w-40 place-items-center rounded-[1.75rem] border border-white/20 bg-[#d63b50] shadow-xl shadow-black/20">
            <span class="ml-2 text-6xl text-white drop-shadow">▶</span>
          </div>
          <span class="absolute -top-5 left-6 rounded-xl border border-white/20 bg-[#5d1825]/90 px-4 py-2 text-sm font-bold text-white shadow-lg rotate-[5deg]">⚗ Science</span>
          <span class="absolute right-[-18px] top-14 rounded-xl border border-white/20 bg-[#5d1825]/90 px-4 py-2 text-sm font-bold text-white shadow-lg rotate-[4deg]">▣ Technology</span>
          <span class="absolute bottom-8 left-[-24px] rounded-xl border border-white/20 bg-[#5d1825]/90 px-4 py-2 text-sm font-bold text-white shadow-lg rotate-[-5deg]">♜ History</span>
          <span class="absolute bottom-[-10px] right-8 rounded-xl border border-white/20 bg-[#5d1825]/90 px-4 py-2 text-sm font-bold text-white shadow-lg">◉ Culture</span>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default { name: "HeroSection" };
</script>
