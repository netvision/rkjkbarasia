<script setup>
import { useRouter } from 'vue-router';
const router = useRouter()

const goTo = (r) => router.push(r) 
</script>
<template>
  <div class="flex p-6 m-6 gap-6">
    <div @click="goTo('students')"
      class="block cursor-pointer rounded-lg bg-white p-6 shadow-[0_2px_15px_-3px_rgba(0,0,0,0.07),0_10px_20px_-2px_rgba(0,0,0,0.04)] dark:bg-neutral-700">
      <h5
        class="mb-2 text-xl font-medium leading-tight text-neutral-800 dark:text-neutral-50">
        Student Information
      </h5>
      <p class="mb-4 text-base text-neutral-600 dark:text-neutral-200">
        Some quick example text to build on the card title and make up the
        bulk of the card's content.
      </p>
    </div>
    <div @click="goTo('staff')"
      class="block cursor-pointer rounded-lg bg-white p-6 shadow-[0_2px_15px_-3px_rgba(0,0,0,0.07),0_10px_20px_-2px_rgba(0,0,0,0.04)] dark:bg-neutral-700">
      <h5
        class="mb-2 text-xl font-medium leading-tight text-neutral-800 dark:text-neutral-50">
        Staff Information
      </h5>
      <p class="mb-4 text-base text-neutral-600 dark:text-neutral-200">
        Some quick example text to build on the card title and make up the
        bulk of the card's content.
      </p>
    </div>
    <div @click="goTo('library')"
      class="block cursor-pointer rounded-lg bg-white p-6 shadow-[0_2px_15px_-3px_rgba(0,0,0,0.07),0_10px_20px_-2px_rgba(0,0,0,0.04)] dark:bg-neutral-700">
      <h5
        class="mb-2 text-xl font-medium leading-tight text-neutral-800 dark:text-neutral-50">
        Library
      </h5>
      <p class="mb-4 text-base text-neutral-600 dark:text-neutral-200">
        Some quick example text to build on the card title and make up the
        bulk of the card's content.
      </p>
    </div>
  </div>
</template>
<route lang="json">
  {
    "meta" : {
      "requireAuth" : true
    }
  }
</route>