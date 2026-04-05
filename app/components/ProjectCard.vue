<script setup lang="ts">
defineProps<{
  title: string
  image: string
  summary?: string
  problem: string
  solution: string
  tech: string
  features?: string[]
  details: string[]
}>()
</script>

<template>
  <article class="rounded-xl border border-gray-800 bg-[#141216] p-6">
    <div class="mb-5 overflow-hidden rounded-xl border border-gray-800 bg-[#100f12]">
      <img
        :src="image"
        :alt="title"
        class="h-48 w-full object-cover"
      >
    </div>

    <h3 class="text-2xl font-semibold text-[#f8f5fc]">
      {{ title }}
    </h3>

    <p v-if="summary" class="mt-3 leading-7 text-[#cfc2dc]">
      {{ summary }}
    </p>

    <div class="mt-5 space-y-4 text-[#ddd5e7]">
      <p class="leading-7">
        <span class="font-semibold text-[#f8f5fc]">Problem:</span>
        {{ problem }}
      </p>

      <p class="leading-7">
        <span class="font-semibold text-[#f8f5fc]">Solution:</span>
        {{ solution }}
      </p>

      <p class="text-sm text-[#aa9bb9]">
        <span class="font-medium text-[#c5b9d3]">Tech:</span>
        {{ tech }}
      </p>
    </div>

    <div v-if="features?.length" class="mt-5">
      <p class="text-sm font-medium text-[#c5b9d3]">
        Key Features
      </p>
      <ul class="mt-3 space-y-2 text-sm text-[#cfc2dc]">
        <li
          v-for="feature in features"
          :key="feature"
          class="flex gap-2"
        >
          <span class="mt-2 h-1.5 w-1.5 shrink-0 rounded-full bg-[#5d1aba]"></span>
          <span>{{ feature }}</span>
        </li>
      </ul>
    </div>

    <details class="group mt-5 rounded-lg border border-gray-800 bg-[#100f12]">
      <summary class="flex cursor-pointer list-none items-center justify-between px-4 py-3 text-sm font-medium text-[#cfc2dc]">
        <span>Technical Details</span>
        <svg
          aria-hidden="true"
          class="h-4 w-4 shrink-0 rotate-90 text-[#cfc2dc] transition-transform duration-200 ease-in-out group-open:rotate-270"
          viewBox="0 0 16 16"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M6 3.5L10.5 8L6 12.5"
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="1.5"
          />
        </svg>
      </summary>
      <div class="border-t border-gray-800 px-4 py-3">
        <ul class="space-y-2 text-sm leading-7 text-[#b8adc6]">
          <li
            v-for="detail in details"
            :key="detail"
            class="flex gap-2"
          >
            <span class="mt-2 h-1.5 w-1.5 shrink-0 rounded-full bg-[#5d1aba]"></span>
            <span>{{ detail }}</span>
          </li>
        </ul>
      </div>
    </details>
  </article>
</template>
