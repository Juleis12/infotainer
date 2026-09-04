<template>
  <div class="mb-8 flex flex-wrap gap-2">
    <button v-for="tag in uniqueTags" :key="tag" type="button" @click="filterByTag(tag)" :class="selectedTags.includes(tag) ? 'border-blue-500 bg-blue-500 text-white shadow-md shadow-blue-500/20' : 'border-slate-200 bg-white text-slate-600 hover:border-blue-300 hover:text-blue-600 dark:border-slate-800 dark:bg-slate-900 dark:text-slate-300 dark:hover:border-blue-700 dark:hover:text-blue-400'" class="rounded-full border px-4 py-2 text-xs font-semibold capitalize transition">
      {{ tag }}
    </button>
  </div>
</template>
<script>
export default {
  name: "TagFilter",
  props: { channels: { type: Array, default: () => [] }, selectedTags: { type: Array, default: () => [] } },
  computed: { uniqueTags() { return Array.from(new Set(this.channels.flatMap((channel) => channel.tags))).sort(); } },
  methods: { filterByTag(tag) { this.$emit("filter", tag); } },
};
</script>
