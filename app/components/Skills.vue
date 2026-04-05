<script setup lang="ts">
defineProps<{
  groups: Array<{
    title: string
    description: string
  }>
}>()
</script>

<template>
  <section id="skills" class="px-6 py-16">
    <h2 class="mb-6 text-3xl font-bold text-[#f8f5fc]">
      Skills
    </h2>

    <div class="grid grid-cols-2 gap-6 text-[#c5b9d3]">
      <div v-for="group in groups" :key="group.title">
        <h3 class="font-semibold text-[#f8f5fc]">
          {{ group.title }}
        </h3>
        <p>{{ group.description }}</p>
      </div>
    </div>
  </section>
</template>
