<template>
  <div class="container mx-auto my-8">
    <!-- Check if sections are available before rendering -->
    <div v-if="sections.length > 0">
      <!-- Tabs for Desktop -->
      <div class="hidden lg:block">
        <div class="border-b">
          <nav class="flex space-x-4" aria-label="Tabs">
            <button
              v-for="(section, index) in sections"
              :key="index"
              @click="activeIndex = index"
              :class="{
                'text-blue-600 border-blue-600': activeIndex === index,
                'text-gray-500 hover:text-gray-700': activeIndex !== index,
              }"
              class="px-3 py-2 font-medium text-sm border-b-2"
            >
              {{ section.title }}
            </button>
          </nav>
        </div>
        <div v-html="sections[activeIndex]?.content" class="p-4"></div>
      </div>

      <!-- Accordion for Mobile -->
      <div class="lg:hidden">
        <div v-for="(section, index) in sections" :key="index" class="border-b">
          <button
            @click="toggleAccordion(index)"
            class="w-full text-left px-4 py-3 flex justify-between items-center"
          >
            <span>{{ section.title }}</span>
            <svg
              :class="activeIndex === index ? 'transform rotate-180' : ''"
              class="w-5 h-5 transition-transform"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M19 9l-7 7-7-7"
              ></path>
            </svg>
          </button>
          <transition name="fade">
            <div v-if="activeIndex === index" class="px-4 py-2 transition-all">
              <div v-html="section.content"></div>
            </div>
          </transition>
        </div>
      </div>
    </div>

    <div v-else>
      <p>Loading content, please wait...</p>
    </div>
  </div>
</template>

<script setup lang="ts">
// eslint-disable-next-line prettier/prettier
import {
  onMounted,
  ref,
} from 'vue';

import data from '@/data/data.json';

const sections = ref([]);
const activeIndex = ref(0);

onMounted(() => {
  if (data && data.length > 0) {
    sections.value = data;
  } else {
    console.error('Failed to load sections data.');
  }
});

function toggleAccordion(index: number) {
  if (activeIndex.value === index) {
    activeIndex.value = -1;
  } else {
    activeIndex.value = index;
  }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
