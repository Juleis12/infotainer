<template>
  <div class="mb-8 flex flex-wrap gap-2">
    <button
      v-for="tag in uniqueTags"
      :key="tag"
      type="button"
      @click="filterByTag(tag)"
      :class="selectedTags.includes(tag) ? 'border-[#c62835] bg-[#c62835] text-white shadow-md shadow-[#b8323a]/20' : 'border-[#e2d4ce] bg-[#fffdfb] text-[#624d49] hover:border-[#d66a64] hover:bg-[#fff6f3] hover:text-[#a52d36] dark:border-[#453031] dark:bg-[#211718] dark:text-[#d9c5c0] dark:hover:border-[#9e3c43] dark:hover:bg-[#2b1b1c] dark:hover:text-[#ef766d]'"
      class="rounded-full border px-4 py-2 text-xs font-bold capitalize transition"
    >
      {{ tag }}
    </button>
  </div>
</template>

<script>
export default {
  name: "TagFilter",
  props: {
    channels: { type: Array, default: () => [] },
    selectedTags: { type: Array, default: () => [] },
  },
  computed: {
    uniqueTags() {
      return Array.from(new Set(this.channels.flatMap((channel) => channel.tags))).sort();
    },
  },
  methods: {
    filterByTag(tag) {
      this.$emit("filter", tag);
    },
  },
};
</script>
