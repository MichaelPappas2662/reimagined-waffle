<template>
  <div class="bg-gray-100 min-h-screen">
    <!-- Header Section with Banner -->
    <header class="relative bg-gray-800 text-white">
      <div
        class="w-full h-[550px] bg-cover bg-center flex items-center justify-center"
        style="background-image: url('https://via.placeholder.com/1920x650')"
      >
        <picture class="w-full h-full">
          <source media="(max-width: 868px)" srcset="https://via.placeholder.com/600x600" />
          <img
            src="https://via.placeholder.com/1920x650"
            alt="Banner Image"
            class="w-full h-full object-cover"
            style="height: 550px"
          />
        </picture>
        <div class="absolute inset-0 flex flex-col justify-center items-center">
          <h1 class="text-5xl font-bold">Hello Developer!</h1>
          <p class="text-xl mt-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit</p>
        </div>
      </div>
    </header>

    <!-- Cards Section -->
    <section class="flex justify-center my-12">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
        <AppCard
          title="Card Title 1"
          content="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        />
        <AppCard
          title="Card Title 2"
          content="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        />
        <AppCard
          title="Card Title 3"
          content="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        />
      </div>
    </section>

    <!-- Tabs/Accordion Section -->
    <section class="my-12">
      <TabsAccordion />
    </section>

    <!-- Bonus Question Section -->
    <section class="my-12">
      <BonusQuestion />
    </section>
  </div>
</template>

<script setup lang="ts">
import AppCard from '@/components/AppCard.vue';
import BonusQuestion from '@/components/BonusQuestion.vue';
import TabsAccordion from '@/components/TabsAccordion.vue';
</script>
