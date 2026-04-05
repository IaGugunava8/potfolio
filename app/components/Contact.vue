<script setup lang="ts">
defineProps<{
  email: string
  availability: string
  links: Array<{
    label: string
    href: string
  }>
}>()
</script>

<template>
  <section id="contact" class="px-6 py-16 text-center">
    <h2 class="mb-4 text-3xl font-bold text-[#f8f5fc]">
      Contact
    </h2>

    <p class="mb-4 text-[#c5b9d3]">
      {{ availability }}
    </p>

    <div class="flex justify-center gap-6 text-[#e5dded]">
      <a class="hover:text-[#5d1aba]" :href="`mailto:${email}`">Email</a>
      <a
        v-for="link in links"
        :key="link.label"
        :href="link.href"
        class="hover:text-[#5d1aba]"
      >
        {{ link.label }}
      </a>
    </div>
  </section>
</template>
