<template>
  <div class="flex justify-center items-center min-h-screen">
    <button
      @click="showModal = true"
      class="bg-blue-500 text-white px-4 py-2 rounded-full hover:bg-blue-600 transition"
    >
      Explain why the result of ('b' + 'a' + + 'a' + 'a').toLowerCase() is banana.
    </button>

    <!-- Modal -->
    <div
      v-if="showModal"
      class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50"
    >
      <div class="bg-white p-6 rounded-lg max-w-md mx-auto">
        <h2 class="text-2xl font-bold mb-4">Explanation</h2>
        <p class="mb-4">
          The expression <code>('b' + 'a' + + 'a' + 'a').toLowerCase()</code> evaluates to 'banana'
          because:
        </p>
        <ul class="list-disc list-inside mb-4">
          <li>('b' + 'a') gives 'ba'.</li>
          <li>
            The expression '+ 'a'' is an attempt to convert the string 'a' into a number, which
            results in NaN (Not a Number).
          </li>
          <li>'ba' + NaN results in 'baNaN'.</li>
          <li>Adding the final 'a' gives 'baNaNa'.</li>
          <li>Finally, <code>.toLowerCase()</code> converts 'baNaNa' to 'banana'.</li>
        </ul>
        <button
          @click="showModal = false"
          class="bg-blue-500 text-white px-4 py-2 rounded-full hover:bg-blue-600 transition"
        >
          Close
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const showModal = ref(false);
</script>
