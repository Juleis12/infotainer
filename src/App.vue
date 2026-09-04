<template>
  <div :class="{ dark: isDarkMode }" class="min-h-screen bg-[#f8f3ee] text-[#2b181b] transition-colors dark:bg-[#170b0f] dark:text-[#fff7f3]">
    <nav class="sticky top-0 z-30 border-b border-[#5b1823]/30 bg-[#4a101b]/95 text-white shadow-lg shadow-[#3f0b15]/10 backdrop-blur dark:bg-[#25080e]/95">
      <div class="mx-auto flex max-w-7xl items-center gap-6 px-4 py-3 sm:px-6 lg:px-8">
        <a href="#top" class="flex items-center gap-3 text-lg font-black tracking-tight">
          <span class="grid h-9 w-9 place-items-center rounded-lg bg-[#d43b4b] text-sm shadow-inner">▶</span>
          Infotainer
        </a>
        <div class="hidden items-center gap-6 text-sm font-semibold text-[#f2dfe0] sm:flex">
          <a href="#top" class="border-b-2 border-[#ff6673] pb-1 text-white">Home</a>
          <a href="#topics" class="transition hover:text-white">Topics</a>
          <a href="#about" class="transition hover:text-white">About</a>
        </div>
        <div class="ml-auto flex items-center gap-2">
          <label class="hidden items-center gap-2 rounded-xl border border-white/15 bg-white/10 px-3 py-2 text-sm text-[#f4dfe0] sm:flex">
            <span aria-hidden="true">⌕</span>
            <input v-model="searchQuery" class="w-44 bg-transparent outline-none placeholder:text-[#d6b5b8]" placeholder="Search channels..." aria-label="Search channels" />
          </label>
          <button type="button" class="grid h-10 w-10 place-items-center rounded-xl border border-white/15 bg-white/10 text-base transition hover:bg-white/15" :aria-label="isDarkMode ? 'Use light mode' : 'Use dark mode'" @click="toggleDarkMode">
            {{ isDarkMode ? "☀" : "☾" }}
          </button>
        </div>
      </div>
    </nav>

    <div id="top"><HeroSection /></div>

    <main id="get-started" class="mx-auto max-w-7xl px-4 pb-16 pt-0 sm:px-6 lg:px-8">
      <section class="-mt-7 relative z-10 mb-9 grid overflow-hidden rounded-[1.5rem] border border-[#eadbd2] bg-[#fffdfb] shadow-[0_14px_40px_rgba(74,16,27,0.10)] dark:border-[#43252b] dark:bg-[#211216] sm:grid-cols-3">
        <div class="flex items-center gap-4 border-b border-[#eadbd2] px-6 py-5 dark:border-[#43252b] sm:border-b-0 sm:border-r">
          <span class="grid h-11 w-11 shrink-0 place-items-center rounded-xl bg-[#f6e6e2] text-xl text-[#a82135] dark:bg-[#3a1d23]">▶</span>
          <div><strong class="block text-xl font-black">{{ channels.length }}+</strong><span class="text-xs font-semibold uppercase tracking-wide text-[#806b68] dark:text-[#bda8a8]">Channels</span></div>
        </div>
        <div class="flex items-center gap-4 border-b border-[#eadbd2] px-6 py-5 dark:border-[#43252b] sm:border-b-0 sm:border-r">
          <span class="grid h-11 w-11 shrink-0 place-items-center rounded-xl bg-[#f6e6e2] text-xl text-[#a82135] dark:bg-[#3a1d23]">▦</span>
          <div><strong class="block text-xl font-black">{{ uniqueTagCount }}+</strong><span class="text-xs font-semibold uppercase tracking-wide text-[#806b68] dark:text-[#bda8a8]">Topics</span></div>
        </div>
        <div class="flex items-center gap-4 px-6 py-5">
          <span class="grid h-11 w-11 shrink-0 place-items-center rounded-xl bg-[#f6e6e2] text-xl text-[#a82135] dark:bg-[#3a1d23]">♧</span>
          <div><strong class="block text-xl font-black">Curious</strong><span class="text-xs font-semibold uppercase tracking-wide text-[#806b68] dark:text-[#bda8a8]">Minds Welcome</span></div>
        </div>
      </section>

      <section id="topics" class="mb-8 flex flex-col gap-4 sm:flex-row sm:items-end sm:justify-between">
        <div>
          <p class="text-xs font-black uppercase tracking-[0.24em] text-[#a82135] dark:text-[#ef777d]">Curated learning</p>
          <h2 class="mt-2 text-3xl font-black tracking-tight">Find your next rabbit hole</h2>
          <p class="mt-1 text-sm text-[#806b68] dark:text-[#bda8a8]">{{ filteredChannels.length }} channels · {{ uniqueTagCount }} topics</p>
        </div>
        <label class="flex items-center gap-2 rounded-xl border border-[#dec9c2] bg-[#fffdfb] px-4 py-2.5 text-sm shadow-sm dark:border-[#4a2c32] dark:bg-[#211216] sm:hidden">
          <span aria-hidden="true">⌕</span>
          <input v-model="searchQuery" class="min-w-0 flex-1 bg-transparent outline-none placeholder:text-[#a18b87]" placeholder="Search channels..." aria-label="Search channels" />
        </label>
      </section>

      <TagFilter :channels="channels" :selectedTags="selectedTags" @filter="applyFilter" />

      <div v-if="filteredChannels.length" class="grid grid-cols-1 gap-5 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
        <CardComponent v-for="channel in filteredChannels" :key="channel.id" :name="channel.name" :description="channel.description" :id="channel.id" :logo="channel.logo" :tags="channel.tags" />
      </div>

      <div v-else class="rounded-[2rem] border border-dashed border-[#d9c1bb] bg-[#fffdfb] p-12 text-center dark:border-[#493038] dark:bg-[#211216]">
        <p class="text-lg font-bold">No channels match your search or topics.</p>
        <button type="button" class="mt-3 text-sm font-bold text-[#a82135] hover:underline dark:text-[#ef777d]" @click="clearFilters">Clear filters</button>
      </div>
    </main>

    <footer id="about" class="border-t border-[#5b1823] bg-[#3b0b16] text-[#f4dfe0] dark:bg-[#21070c]">
      <div class="mx-auto flex max-w-7xl flex-col gap-8 px-4 py-10 sm:px-6 lg:flex-row lg:items-center lg:justify-between lg:px-8">
        <div>
          <div class="flex items-center gap-3 text-lg font-black"><span class="grid h-8 w-8 place-items-center rounded-lg bg-[#d43b4b] text-xs">▶</span>Infotainer</div>
          <p class="mt-2 max-w-sm text-sm text-[#d9bfc2]">A curated directory of educational YouTube channels.</p>
        </div>
        <div class="flex gap-6 text-sm font-semibold text-[#ead3d5]"><a href="#about" class="hover:text-white">About</a><a href="#topics" class="hover:text-white">Sources</a><a href="#get-started" class="hover:text-white">Contribute</a><a href="mailto:hello@infotainer.tchh.in" class="hover:text-white">Feedback</a></div>
        <p class="text-sm text-[#ead3d5]">♥ Made for curious minds.</p>
      </div>
    </footer>
  </div>
</template>

<script>
import CardComponent from "./components/CardComponent.vue";
import HeroSection from "./components/HeroSection.vue";
import TagFilter from "./components/TagFilter.vue";
import channels from "./data/channels";

export default {
  name: "App",
  components: { CardComponent, HeroSection, TagFilter },
  data() {
    return { channels: [], isDarkMode: false, selectedTags: [], searchQuery: "" };
  },
  computed: {
    filteredChannels() {
      const query = this.searchQuery.trim().toLowerCase();
      return this.channels.filter((channel) => {
        const matchesTags = !this.selectedTags.length || this.selectedTags.every((tag) => channel.tags.includes(tag));
        const matchesSearch = !query || `${channel.name} ${channel.description} ${channel.tags.join(" ")}`.toLowerCase().includes(query);
        return matchesTags && matchesSearch;
      });
    },
    uniqueTagCount() {
      return new Set(this.channels.flatMap((channel) => channel.tags)).size;
    },
  },
  mounted() {
    this.channels = [...channels].sort((a, b) => a.name.localeCompare(b.name));
    this.isDarkMode = localStorage.getItem("infotainer-theme") === "dark";
    document.documentElement.classList.toggle("dark", this.isDarkMode);
  },
  methods: {
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode;
      document.documentElement.classList.toggle("dark", this.isDarkMode);
      localStorage.setItem("infotainer-theme", this.isDarkMode ? "dark" : "light");
    },
    applyFilter(tag) {
      this.selectedTags = this.selectedTags.includes(tag) ? this.selectedTags.filter((item) => item !== tag) : [...this.selectedTags, tag];
    },
    clearFilters() {
      this.selectedTags = [];
      this.searchQuery = "";
    },
  },
};
</script>
