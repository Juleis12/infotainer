<template>
  <div :class="{ dark: isDarkMode }" class="min-h-screen bg-slate-50 text-slate-900 transition-colors dark:bg-slate-950 dark:text-slate-100">
    <HeroSection />
    <main id="get-started" class="mx-auto max-w-7xl px-4 pb-16 pt-8 sm:px-6 lg:px-8">
      <section class="mb-8 flex flex-col gap-4 rounded-3xl border border-slate-200/80 bg-white/80 p-5 shadow-sm backdrop-blur dark:border-slate-800 dark:bg-slate-900/80 sm:flex-row sm:items-center sm:justify-between">
        <div><p class="text-sm font-medium uppercase tracking-widest text-blue-600 dark:text-blue-400">Curated learning</p><h2 class="mt-1 text-2xl font-bold tracking-tight">Find your next rabbit hole</h2><p class="mt-1 text-sm text-slate-500 dark:text-slate-400">{{ filteredChannels.length }} channels · {{ uniqueTagCount }} topics</p></div>
        <button type="button" class="rounded-full border border-slate-200 bg-slate-50 px-4 py-2 text-sm font-semibold text-slate-700 transition hover:border-blue-300 hover:text-blue-600 dark:border-slate-700 dark:bg-slate-800 dark:text-slate-200 dark:hover:border-blue-500 dark:hover:text-blue-400" @click="toggleDarkMode">{{ isDarkMode ? "☀ Light mode" : "☾ Dark mode" }}</button>
      </section>
      <TagFilter :channels="channels" :selectedTags="selectedTags" @filter="applyFilter" />
      <div v-if="filteredChannels.length" class="grid grid-cols-1 gap-5 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
        <CardComponent v-for="channel in filteredChannels" :key="channel.id" :name="channel.name" :description="channel.description" :id="channel.id" :logo="channel.logo" :tags="channel.tags" />
      </div>
      <div v-else class="rounded-3xl border border-dashed border-slate-300 p-12 text-center dark:border-slate-700"><p class="text-lg font-semibold">No channels match those topics.</p><button class="mt-3 text-sm font-semibold text-blue-600 hover:underline dark:text-blue-400" @click="selectedTags = []">Clear filters</button></div>
    </main>
  </div>
</template>
<script>
import CardComponent from "./components/CardComponent.vue";
import HeroSection from "./components/HeroSection.vue";
import TagFilter from "./components/TagFilter.vue";
import channels from "./data/channels";
export default {
  name: "App", components: { CardComponent, HeroSection, TagFilter },
  data() { return { channels: [], isDarkMode: false, selectedTags: [] }; },
  computed: {
    filteredChannels() { if (!this.selectedTags.length) return this.channels; return this.channels.filter((channel) => this.selectedTags.every((tag) => channel.tags.includes(tag))); },
    uniqueTagCount() { return new Set(this.channels.flatMap((channel) => channel.tags)).size; },
  },
  mounted() { this.channels = [...channels].sort((a, b) => a.name.localeCompare(b.name)); this.isDarkMode = localStorage.getItem("infotainer-theme") === "dark"; document.documentElement.classList.toggle("dark", this.isDarkMode); },
  methods: {
    toggleDarkMode() { this.isDarkMode = !this.isDarkMode; document.documentElement.classList.toggle("dark", this.isDarkMode); localStorage.setItem("infotainer-theme", this.isDarkMode ? "dark" : "light"); },
    applyFilter(tag) { this.selectedTags = this.selectedTags.includes(tag) ? this.selectedTags.filter((item) => item !== tag) : [...this.selectedTags, tag]; },
  },
};
</script>
