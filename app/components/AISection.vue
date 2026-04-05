<script setup lang="ts">
defineProps<{
  items: string[]
}>()
</script>

<template>
  <section id="systems" class="px-6 py-16">
    <h2 class="mb-6 text-3xl font-bold text-[#f8f5fc]">
      AI Engineering Approach
    </h2>

    <ul class="list-disc space-y-3 pl-6 text-[#c5b9d3] marker:text-[#5d1aba]">
      <li v-for="item in items" :key="item">
        {{ item }}
      </li>
    </ul>
  </section>
</template>
