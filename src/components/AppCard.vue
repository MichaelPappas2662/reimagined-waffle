<template>
  <div class="bg-white rounded-lg shadow-lg overflow-hidden" style="width: 320px">
    <div class="flex justify-center">
      <img
        src="https://via.placeholder.com/400x300"
        alt="Placeholder"
        class="object-contain"
        style="padding: 20px"
      />
    </div>
    <div class="p-4 flex flex-col justify-between h-52">
      <div>
        <p class="text-gray-700 text-sm">{{ content }}</p>
      </div>
      <button
        class="mt-4 bg-blue-500 text-white px-4 py-2 rounded-full hover:bg-blue-600 transition self-center"
      >
        READ MORE
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue';

interface CardProps {
  content: string;
}

defineProps<CardProps>();
</script>
