<template>
  <header class="relative isolate overflow-hidden border-b border-slate-200 bg-slate-950 text-white dark:border-slate-800">
    <img src="../assets/bg3.jpg" alt="" class="absolute inset-0 -z-20 h-full w-full object-cover opacity-45" />
    <div class="absolute inset-0 -z-10 bg-gradient-to-br from-slate-950 via-slate-950/90 to-blue-950/70"></div>
    <div class="mx-auto max-w-7xl px-4 py-20 sm:px-6 sm:py-28 lg:px-8">
      <div class="max-w-3xl">
        <span class="inline-flex items-center rounded-full border border-white/15 bg-white/10 px-3 py-1 text-xs font-semibold uppercase tracking-[0.2em] text-blue-200 backdrop-blur">
          Infotainer
        </span>
        <h1 class="mt-6 text-5xl font-black tracking-tight sm:text-6xl lg:text-7xl">
          Learn something worth talking about.
        </h1>
        <p class="mt-6 max-w-2xl text-lg leading-8 text-slate-300 sm:text-xl">
          A curated collection of YouTube channels for science, culture, business, philosophy, technology and curious minds.
        </p>
        <a href="#get-started" class="mt-8 inline-flex rounded-full bg-blue-500 px-6 py-3 text-sm font-bold text-white shadow-lg shadow-blue-500/20 transition hover:-translate-y-0.5 hover:bg-blue-400">
          Explore channels ↓
        </a>
      </div>
    </div>
  </header>
</template>

<script>
export default { name: "HeroSection" };
</script>
