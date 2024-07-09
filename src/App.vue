<template>
  <div class="min-h-screen">
    <h1 class="mt-6 text-5xl font-extrabold text-gray-200" :class="{ 'squiggly-underline': submitted }">Pet Stories</h1>
    <div v-if="!submitted" class="md:grid grid-cols-2 gap-16 mt-24 items-center">
      <div>
        <h2 class="text-3xl font-semibold">Get Updates</h2>
        <form name="pet-stories-email" data-netlify="true" @submit.prevent="submitForm" class="mt-8">
          <label
            class="flex items-center gap-2 input input-bordered focus-within:outline-none focus-within:ring-0 focus-within:border-primary">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16" fill="currentColor" class="h-4 w-4 opacity-70">
              <path
                d="M2.5 3A1.5 1.5 0 0 0 1 4.5v.793c.026.009.051.02.076.032L7.674 8.51c.206.1.446.1.652 0l6.598-3.185A.755.755 0 0 1 15 5.293V4.5A1.5 1.5 0 0 0 13.5 3h-11Z" />
              <path
                d="M15 6.954 8.978 9.86a2.25 2.25 0 0 1-1.956 0L1 6.954V11.5A1.5 1.5 0 0 0 2.5 13h11a1.5 1.5 0 0 0 1.5-1.5V6.954Z" />
            </svg>
            <input type="email" placeholder="Email"
              class="grow bg-transparent border-none focus:outline-none focus:ring-0 w-full" />
          </label>
          <button type="submit" class="btn btn-primary block mt-4 w-full">Submit</button>
        </form>
      </div>
      <img src="/one-liner.jpeg" alt="Pet Image" class="rounded-lg shadow-md w-full h-auto mt-8 md:mt-0">
    </div>
    <transition name="fade">
      <div v-if="submitted" class="md:grid grid-cols-2 gap-16 mt-24 items-center">
        <div>
          <h2 class="text-3xl font-semibold">Thank you for your support! 🎊</h2>
          <p class="mt-4">You're all set! You'll receive updates from us soon.</p>
        </div>
        <img src="/Mako2.jpeg" alt="Pet Image" class="rounded-lg shadow-md w-full h-auto mt-8 md:mt-0">
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import confetti from 'canvas-confetti'

const submitted = ref(false)

const submitForm = () => {
  confetti({
    particleCount: 200,
    spread: 80,
    origin: { y: 0.6 }
  })
  submitted.value = true
}
</script>
<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.squiggly-underline {
  display: inline-block;
  position: relative;
  padding-bottom: 12px;
}

.squiggly-underline::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 12px;
  background-image: url("data:image/svg+xml,%3Csvg width='100' height='12' viewBox='0 0 100 12' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M0 6C8.33333 1.33333 16.6667 1.33333 25 6C33.3333 10.6667 41.6667 10.6667 50 6C58.3333 1.33333 66.6667 1.33333 75 6C83.3333 10.6667 91.6667 10.6667 100 6' stroke='%237582ff' stroke-width='2'/%3E%3C/svg%3E");
  background-repeat: repeat-x;
  background-size: 100px 12px;
  animation: squiggle 3s linear infinite;
}

@keyframes squiggle {
  from {
    background-position: 0 0;
  }

  to {
    background-position: 100px 0;
  }
}
</style>