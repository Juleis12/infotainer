<template>
  <div :class="{ dark: isDarkMode }" class="min-h-screen bg-[#f7f3ef] text-[#241b1b] transition-colors dark:bg-[#160f10] dark:text-[#f8efea]">
    <HeroSection />
    <main id="get-started" class="mx-auto max-w-7xl px-4 pb-16 pt-10 sm:px-6 lg:px-8">
      <section class="mb-8 flex flex-col gap-5 rounded-[2rem] border border-[#e7d9d2] bg-[#fffdfb] p-6 shadow-[0_10px_35px_rgba(110,40,35,0.07)] dark:border-[#3b2929] dark:bg-[#211718] sm:flex-row sm:items-center sm:justify-between">
        <div>
          <p class="text-xs font-bold uppercase tracking-[0.22em] text-[#b8323a] dark:text-[#ef766d]">Curated learning</p>
          <h2 class="mt-2 text-2xl font-black tracking-tight text-[#241b1b] dark:text-[#fff7f3]">Find your next rabbit hole</h2>
          <p class="mt-1 text-sm text-[#806f6a] dark:text-[#bdaaa5]">{{ filteredChannels.length }} channels · {{ uniqueTagCount }} topics</p>
        </div>
        <button type="button" class="rounded-full border border-[#dfc9c2] bg-[#f8f1ed] px-4 py-2 text-sm font-bold text-[#5c4140] transition hover:border-[#c94b4d] hover:bg-[#fff5f2] hover:text-[#a52d36] dark:border-[#4a3031] dark:bg-[#2a1c1d] dark:text-[#ead8d3] dark:hover:border-[#b94a50] dark:hover:text-[#ef766d]" @click="toggleDarkMode">
          {{ isDarkMode ? "☀ Light mode" : "☾ Dark mode" }}
        </button>
      </section>

      <TagFilter :channels="channels" :selectedTags="selectedTags" @filter="applyFilter" />

      <div v-if="filteredChannels.length" class="grid grid-cols-1 gap-5 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
        <CardComponent v-for="channel in filteredChannels" :key="channel.id" :name="channel.name" :description="channel.description" :id="channel.id" :logo="channel.logo" :tags="channel.tags" />
      </div>

      <div v-else class="rounded-[2rem] border border-dashed border-[#d9c3bd] bg-[#fffdfb] p-12 text-center dark:border-[#493233] dark:bg-[#211718]">
        <p class="text-lg font-bold">No channels match those topics.</p>
        <button type="button" class="mt-3 text-sm font-bold text-[#b8323a] hover:underline dark:text-[#ef766d]" @click="selectedTags = []">Clear filters</button>
      </div>
    </main>
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
    return { channels: [], isDarkMode: false, selectedTags: [] };
  },
  computed: {
    filteredChannels() {
      if (!this.selectedTags.length) return this.channels;
      return this.channels.filter((channel) => this.selectedTags.every((tag) => channel.tags.includes(tag)));
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
      this.selectedTags = this.selectedTags.includes(tag)
        ? this.selectedTags.filter((item) => item !== tag)
        : [...this.selectedTags, tag];
    },
  },
};
</script>
