<template>
  <header class="relative isolate overflow-hidden border-b border-[#e7d9d2] bg-[#211718] text-[#fffaf7] dark:border-[#3b2929] dark:bg-[#120b0c]">
    <img src="../assets/bg3.jpg" alt="" class="absolute inset-0 -z-20 h-full w-full object-cover opacity-20 mix-blend-luminosity" />
    <div class="absolute inset-0 -z-10 bg-[radial-gradient(circle_at_78%_38%,rgba(200,55,61,0.38),transparent_32%),linear-gradient(115deg,#211718_0%,#2b1718_52%,#8f2d35_150%)]"></div>
    <div class="mx-auto max-w-7xl px-4 py-20 sm:px-6 sm:py-28 lg:px-8">
      <div class="max-w-3xl">
        <span class="inline-flex items-center rounded-full border border-[#e97b70]/30 bg-[#e97b70]/10 px-3 py-1 text-xs font-bold uppercase tracking-[0.22em] text-[#f5aaa0]">
          Infotainer
        </span>
        <h1 class="mt-6 text-5xl font-black leading-[0.95] tracking-[-0.04em] sm:text-6xl lg:text-7xl">
          Learn something<br /><span class="text-[#f06a62]">worth talking about.</span>
        </h1>
        <p class="mt-6 max-w-2xl text-lg leading-8 text-[#e5d5d0] sm:text-xl">
          A curated collection of YouTube channels for science, culture, business, philosophy, technology and curious minds.
        </p>
        <a href="#get-started" class="mt-8 inline-flex items-center rounded-xl bg-[#c62835] px-6 py-3 text-sm font-black text-white shadow-lg shadow-[#7f2028]/30 transition hover:-translate-y-0.5 hover:bg-[#d73a45] focus:outline-none focus:ring-2 focus:ring-[#f06a62] focus:ring-offset-2 focus:ring-offset-[#211718]">
          Explore channels <span class="ml-2">↓</span>
        </a>
      </div>
    </div>
  </header>
</template>

<script>
export default { name: "HeroSection" };
</script>
