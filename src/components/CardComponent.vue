<template>
  <article class="group flex h-full flex-col overflow-hidden rounded-[1.5rem] border border-[#e5d8d2] bg-[#fffdfb] p-5 shadow-[0_8px_24px_rgba(91,42,38,0.06)] transition duration-300 hover:-translate-y-1 hover:border-[#d77970] hover:shadow-[0_16px_38px_rgba(151,47,50,0.12)] dark:border-[#3e2b2c] dark:bg-[#211718] dark:hover:border-[#7f3a3e] dark:hover:shadow-black/20">
    <div class="flex items-start gap-4">
      <img :src="logo" :alt="`${name} logo`" class="h-16 w-16 shrink-0 rounded-2xl border border-[#eaded8] bg-[#f5eee9] object-cover shadow-sm transition duration-300 group-hover:scale-105 dark:border-[#4a3435] dark:bg-[#2a1c1d]" />
      <div class="min-w-0 flex-1">
        <h2 class="text-base font-black leading-6 text-[#241b1b] dark:text-white">
          <a :href="channelUrl" target="_blank" rel="noopener noreferrer" class="transition hover:text-[#b8323a] dark:hover:text-[#ef766d]">{{ name }}</a>
        </h2>
        <a :href="channelUrl" target="_blank" rel="noopener noreferrer" class="mt-1 inline-block text-xs font-bold text-[#b8323a] dark:text-[#ef766d]">Watch on YouTube ↗</a>
      </div>
    </div>
    <div class="mt-5 flex flex-wrap gap-1.5">
      <span v-for="tag in tags" :key="tag" class="rounded-full bg-[#f3e9e4] px-2.5 py-1 text-[11px] font-bold text-[#6b514d] dark:bg-[#302021] dark:text-[#d8c0bb]">{{ tag }}</span>
    </div>
    <p class="mt-4 flex-1 whitespace-pre-line text-sm leading-6 text-[#76635f] dark:text-[#bdaaa5]">{{ truncatedDescription }}<button v-if="isTruncated" type="button" class="ml-1 font-black text-[#b8323a] hover:underline dark:text-[#ef766d]" @click="toggleDescription">{{ showFullDescription ? "Less" : "More" }}</button></p>
  </article>
</template>

<script>
const descriptionSize = 120;

export default {
  name: "CardComponent",
  props: {
    id: String,
    name: String,
    description: String,
    logo: String,
    tags: { type: Array, default: () => [] },
  },
  data() {
    return { showFullDescription: false };
  },
  computed: {
    channelUrl() {
      return `https://www.youtube.com/${this.id}`;
    },
    isTruncated() {
      return this.description.length > descriptionSize;
    },
    truncatedDescription() {
      return this.showFullDescription || !this.isTruncated ? this.description : `${this.description.substring(0, descriptionSize)}...`;
    },
  },
  methods: {
    toggleDescription() {
      this.showFullDescription = !this.showFullDescription;
    },
  },
};
</script>
