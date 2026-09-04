<template>
  <article class="group flex h-full flex-col overflow-hidden rounded-[1.25rem] border border-[#eadbd2] bg-[#fffdfb] shadow-[0_8px_24px_rgba(74,16,27,0.07)] transition duration-300 hover:-translate-y-1 hover:border-[#c87980] hover:shadow-[0_18px_40px_rgba(126,24,45,0.14)] dark:border-[#43262c] dark:bg-[#211216] dark:hover:border-[#82404b]">
    <div class="h-2 bg-gradient-to-r from-[#5d1020] via-[#b51f39] to-[#df5968]"></div>
    <div class="flex flex-1 flex-col p-5">
      <div class="flex items-start gap-4">
        <img :src="logo" :alt="`${name} logo`" class="h-16 w-16 shrink-0 rounded-2xl border border-[#eaded8] bg-[#f5eee9] object-cover shadow-sm transition duration-300 group-hover:scale-105 dark:border-[#4a3438] dark:bg-[#2a191e]" />
        <div class="min-w-0 flex-1">
          <h2 class="text-base font-black leading-6 text-[#28191b] dark:text-white">
            <a :href="channelUrl" target="_blank" rel="noopener noreferrer" class="transition hover:text-[#a82135] dark:hover:text-[#ef777d]">{{ name }}</a>
          </h2>
          <a :href="channelUrl" target="_blank" rel="noopener noreferrer" class="mt-1 inline-block text-xs font-bold text-[#a82135] dark:text-[#ef777d]">YouTube channel ↗</a>
        </div>
      </div>
      <div class="mt-5 flex flex-wrap gap-1.5">
        <span v-for="tag in tags" :key="tag" class="rounded-full bg-[#f3e7e2] px-2.5 py-1 text-[11px] font-bold text-[#69484c] dark:bg-[#321b22] dark:text-[#dcbfc4]">{{ tag }}</span>
      </div>
      <p class="mt-4 flex-1 whitespace-pre-line text-sm leading-6 text-[#76635f] dark:text-[#bda8ad]">{{ truncatedDescription }}<button v-if="isTruncated" type="button" class="ml-1 font-black text-[#a82135] hover:underline dark:text-[#ef777d]" @click="toggleDescription">{{ showFullDescription ? "Less" : "More" }}</button></p>
      <a :href="channelUrl" target="_blank" rel="noopener noreferrer" class="mt-5 inline-flex items-center justify-center rounded-lg bg-[#b51f39] px-4 py-2.5 text-sm font-black text-white shadow-md shadow-[#6f1426]/15 transition hover:bg-[#c72d48] focus:outline-none focus:ring-2 focus:ring-[#e35d6c] focus:ring-offset-2 dark:focus:ring-offset-[#211216]">Visit Channel <span class="ml-2">↗</span></a>
    </div>
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
