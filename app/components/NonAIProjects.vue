<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/pagination'

defineProps<{
  items: Array<{
    title: string
    image: string
    summary: string
    tech: string
    href: string
  }>
}>()

const modules = [Pagination]
</script>

<template>
  <section id="non-ai-projects" class="space-y-8">
    <div class="space-y-3">
      <h2 class="text-3xl font-bold text-[#f8f5fc]">
        Non-AI Projects
      </h2>
      <p class="max-w-2xl text-[#c5b9d3]">
        A few product and engineering builds outside the AI lane.
      </p>
    </div>

    <Swiper
      :modules="modules"
      :pagination="{ clickable: true }"
      :space-between="24"
      :breakpoints="{
        0: { slidesPerView: 1.05 },
        768: { slidesPerView: 2.1 },
        1200: { slidesPerView: 2.6 }
      }"
      class="non-ai-swiper !overflow-visible"
    >
      <SwiperSlide
        v-for="project in items"
        :key="project.title"
        class="h-auto"
      >
        <a
          :href="project.href"
          class="block h-full rounded-xl focus-visible:outline-2 focus-visible:outline-offset-4 focus-visible:outline-[#5d1aba]"
          target="_blank"
          rel="noreferrer"
        >
          <article class="flex h-full flex-col rounded-xl border border-gray-800 bg-[#141216] p-6 transition-transform duration-200 hover:-translate-y-1 hover:border-[#5d1aba]/60">
            <div class="mb-5 overflow-hidden rounded-xl border border-gray-800 bg-[#100f12]">
              <img
                :src="project.image"
                :alt="project.title"
                class="h-44 w-full object-cover"
              >
            </div>

            <h3 class="text-2xl font-semibold text-[#f8f5fc]">
              {{ project.title }}
            </h3>

            <p class="mt-4 flex-1 leading-7 text-[#ddd5e7]">
              {{ project.summary }}
            </p>

            <p class="mt-5 text-sm text-[#aa9bb9]">
              <span class="font-medium text-[#c5b9d3]">Tech:</span>
              {{ project.tech }}
            </p>
          </article>
        </a>
      </SwiperSlide>
    </Swiper>
  </section>
</template>

<style scoped>
:deep(.swiper-pagination) {
  position: static;
  margin-top: 1.5rem;
}

:deep(.swiper-pagination-bullet) {
  width: 0.65rem;
  height: 0.65rem;
  background: rgba(248, 245, 252, 0.22);
  opacity: 1;
}

:deep(.swiper-pagination-bullet-active) {
  background: #5d1aba;
}
</style>
