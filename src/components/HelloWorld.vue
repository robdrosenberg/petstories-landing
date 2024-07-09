<template>
  <div class="min-h-screen flex items-center justify-center px-4">
    <div class="max-w-lg w-full space-y-8">
      <h2 class="mt-6 text-3xl font-extrabold text-gray-200">Pet Stories</h2>
      <form class="mt-8 space-y-6" @submit.prevent="submitForm" data-netlify="true" name="pet-stories-updates">
        <input type="hidden" name="form-name" value="pet-stories-updates" />
        <div>
          <label for="email" class="sr-only">Email address</label>
          <input id="email" name="email" type="email" required
            class="appearance-none rounded-md relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
            placeholder="Email address" v-model="email">
        </div>
        <div>
          <button type="submit"
            class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
            Get Updates
          </button>
        </div>
      </form>
      <div class="mt-8">
        <img src="/Mako1.jpeg" alt="Pet Image" class="rounded-lg shadow-md w-full h-auto">
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import confetti from 'canvas-confetti'

const submitted = ref(false)

const submitForm = () => {
  confetti({
    particleCount: 100,
    spread: 70,
    origin: { y: 0.6 }
  })
  submitted.value = true
}
</script>