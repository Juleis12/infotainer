<template>
  <article class="group flex h-full flex-col overflow-hidden rounded-3xl border border-slate-200 bg-white p-5 shadow-sm transition duration-300 hover:-translate-y-1 hover:border-blue-200 hover:shadow-xl hover:shadow-slate-200/60 dark:border-slate-800 dark:bg-slate-900 dark:hover:border-blue-900 dark:hover:shadow-black/20">
    <div class="flex items-start gap-4">
      <img :src="logo" :alt="`${name} logo`" class="h-16 w-16 shrink-0 rounded-2xl border border-slate-100 object-cover shadow-sm transition duration-300 group-hover:scale-105 dark:border-slate-700" />
      <div class="min-w-0 flex-1">
        <h2 class="text-base font-bold leading-6 text-slate-900 dark:text-white"><a :href="channelUrl" target="_blank" rel="noopener noreferrer" class="hover:text-blue-600 dark:hover:text-blue-400">{{ name }}</a></h2>
        <a :href="channelUrl" target="_blank" rel="noopener noreferrer" class="mt-1 inline-block text-xs font-semibold text-blue-600 dark:text-blue-400">Watch on YouTube ↗</a>
      </div>
    </div>
    <div class="mt-5 flex flex-wrap gap-1.5">
      <span v-for="tag in tags" :key="tag" class="rounded-full bg-slate-100 px-2.5 py-1 text-[11px] font-semibold text-slate-600 dark:bg-slate-800 dark:text-slate-300">{{ tag }}</span>
    </div>
    <p class="mt-4 flex-1 whitespace-pre-line text-sm leading-6 text-slate-500 dark:text-slate-400">{{ truncatedDescription }}<button v-if="isTruncated" type="button" class="ml-1 font-bold text-blue-600 hover:underline dark:text-blue-400" @click="toggleDescription">{{ showFullDescription ? "Less" : "More" }}</button></p>
  </article>
</template>
<script>
const descriptionSize = 120;
export default {
  name: "CardComponent",
  props: { id: String, name: String, description: String, logo: String, tags: { type: Array, default: () => [] } },
  data() { return { showFullDescription: false }; },
  computed: {
    channelUrl() { return `https://www.youtube.com/${this.id}`; },
    isTruncated() { return this.description.length > descriptionSize; },
    truncatedDescription() { return this.showFullDescription || !this.isTruncated ? this.description : `${this.description.substring(0, descriptionSize)}...`; },
  },
  methods: { toggleDescription() { this.showFullDescription = !this.showFullDescription; } },
};
</script>
