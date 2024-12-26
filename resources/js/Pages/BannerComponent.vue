<template>
    <div class="space-y-4">
      <div v-for="(variation, index) in variations" :key="index" class="bg-white rounded-lg shadow-md w-full">
        <div class="p-4 bg-gray-50 border-b">
          <h3 class="text-lg font-semibold text-gray-800">{{ variation.name }}</h3>
        </div>
        <div class="p-4">
          <div class="mb-4">
            <div class="p-4 bg-gray-50 rounded-md" v-html="variation.html"></div>
          </div>
          <div>
            <button
              @click="toggleCode(index)"
              class="px-4 py-2 text-sm font-medium text-blue-600 bg-blue-100 rounded-md hover:bg-blue-200 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2"
            >
              {{ showCode[index] ? 'Hide Code' : 'Show Code' }}
            </button>
          </div>
          <div v-show="showCode[index]" class="mt-4">
            <pre class="p-4 bg-gray-800 rounded-md overflow-x-auto">
              <code class="text-sm text-white">{{ variation.html }}</code>
            </pre>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { X, AlertTriangle, Info } from 'lucide-vue-next'
  
  const showCode = ref({})
  
  const variations = [
    {
      name: 'With button',
      html: `
      <div class="relative isolate flex items-center gap-x-6 overflow-hidden bg-gray-50 px-6 py-2.5 sm:px-3.5 sm:before:flex-1">
  <div class="absolute left-[max(-7rem,calc(50%-52rem))] top-1/2 -z-10 -translate-y-1/2 transform-gpu blur-2xl" aria-hidden="true">
    <div class="aspect-[577/310] w-[36.0625rem] bg-gradient-to-r from-[#ff80b5] to-[#9089fc] opacity-30" style="clip-path: polygon(74.8% 41.9%, 97.2% 73.2%, 100% 34.9%, 92.5% 0.4%, 87.5% 0%, 75% 28.6%, 58.5% 54.6%, 50.1% 56.8%, 46.9% 44%, 48.3% 17.4%, 24.7% 53.9%, 0% 27.9%, 11.9% 74.2%, 24.9% 54.1%, 68.6% 100%, 74.8% 41.9%)"></div>
  </div>
  <div class="absolute left-[max(45rem,calc(50%+8rem))] top-1/2 -z-10 -translate-y-1/2 transform-gpu blur-2xl" aria-hidden="true">
    <div class="aspect-[577/310] w-[36.0625rem] bg-gradient-to-r from-[#ff80b5] to-[#9089fc] opacity-30" style="clip-path: polygon(74.8% 41.9%, 97.2% 73.2%, 100% 34.9%, 92.5% 0.4%, 87.5% 0%, 75% 28.6%, 58.5% 54.6%, 50.1% 56.8%, 46.9% 44%, 48.3% 17.4%, 24.7% 53.9%, 0% 27.9%, 11.9% 74.2%, 24.9% 54.1%, 68.6% 100%, 74.8% 41.9%)"></div>
  </div>
  <div class="flex flex-wrap items-center gap-x-4 gap-y-2">
    <p class="text-sm/6 text-gray-900">
      <strong class="font-semibold">GeneriCon 2023</strong><svg viewBox="0 0 2 2" class="mx-2 inline size-0.5 fill-current" aria-hidden="true"><circle cx="1" cy="1" r="1" /></svg>Join us in Denver from June 7 – 9 to see what’s coming next.
    </p>
    <a href="#" class="flex-none rounded-full bg-gray-900 px-3.5 py-1 text-sm font-semibold text-white shadow-sm hover:bg-gray-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-gray-900">Register now <span aria-hidden="true">&rarr;</span></a>
  </div>
  <div class="flex flex-1 justify-end">
    <button type="button" class="-m-3 p-3 focus-visible:outline-offset-[-4px]">
      <span class="sr-only">Dismiss</span>
      <svg class="size-5 text-gray-900" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true" data-slot="icon">
        <path d="M6.28 5.22a.75.75 0 0 0-1.06 1.06L8.94 10l-3.72 3.72a.75.75 0 1 0 1.06 1.06L10 11.06l3.72 3.72a.75.75 0 1 0 1.06-1.06L11.06 10l3.72-3.72a.75.75 0 0 0-1.06-1.06L10 8.94 6.28 5.22Z" />
      </svg>
    </button>
  </div>
</div>
      `
    },
    {
      name: 'On dark',
      html: `
        <div class="flex items-center gap-x-6 bg-gray-900 px-6 py-2.5 sm:px-3.5 sm:before:flex-1">
          <p class="text-sm leading-6 text-white">
            <strong class="font-semibold">GeneriCon 2023</strong><svg viewBox="0 0 2 2" class="mx-2 inline h-0.5 w-0.5 fill-current" aria-hidden="true"><circle cx="1" cy="1" r="1" /></svg>Join us in Denver from June 7 – 9 to see what's coming next.
          </p>
          <div class="flex flex-1 justify-end">
            <button type="button" class="-m-3 p-3 focus-visible:outline-offset-[-4px]">
              <span class="sr-only">Dismiss</span>
              <X class="h-5 w-5 text-white" aria-hidden="true" />
            </button>
          </div>
        </div>
      `
    },
    {
      name: 'On brand',
      html: `
        <div class="flex items-center justify-between gap-x-6 bg-indigo-600 px-6 py-2.5 sm:pr-3.5 sm:pl-4">
          <p class="text-sm leading-6 text-white">
            <strong class="font-semibold">GeneriCon 2023</strong><svg viewBox="0 0 2 2" class="mx-2 inline h-0.5 w-0.5 fill-current" aria-hidden="true"><circle cx="1" cy="1" r="1" /></svg>Join us in Denver from June 7 – 9 to see what's coming next.
          </p>
          <a href="#" class="flex-none rounded-full bg-indigo-500 px-3.5 py-1 text-sm font-semibold text-white shadow-sm hover:bg-indigo-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-500">Register now <span aria-hidden="true">&rarr;</span></a>
        </div>
      `
    },
    {
      name: 'With background glow',
      html: `
        <div class="relative isolate flex items-center gap-x-6 overflow-hidden bg-gray-50 px-6 py-2.5 sm:px-3.5 sm:before:flex-1">
          <div class="absolute left-[max(-7rem,calc(50%-52rem))] top-1/2 -z-10 -translate-y-1/2 transform-gpu blur-2xl" aria-hidden="true">
            <div class="aspect-[577/310] w-[36.0625rem] bg-gradient-to-r from-[#ff80b5] to-[#9089fc] opacity-30" style="clip-path: polygon(74.8% 41.9%, 97.2% 73.2%, 100% 34.9%, 92.5% 0.4%, 87.5% 0%, 75% 28.6%, 58.5% 54.6%, 50.1% 56.8%, 46.9% 44%, 48.3% 17.4%, 24.7% 53.9%, 0% 27.9%, 11.9% 74.2%, 24.9% 54.1%, 68.6% 100%, 74.8% 41.9%)"></div>
          </div>
          <div class="absolute left-[max(45rem,calc(50%+8rem))] top-1/2 -z-10 -translate-y-1/2 transform-gpu blur-2xl" aria-hidden="true">
            <div class="aspect-[577/310] w-[36.0625rem] bg-gradient-to-r from-[#ff80b5] to-[#9089fc] opacity-30" style="clip-path: polygon(74.8% 41.9%, 97.2% 73.2%, 100% 34.9%, 92.5% 0.4%, 87.5% 0%, 75% 28.6%, 58.5% 54.6%, 50.1% 56.8%, 46.9% 44%, 48.3% 17.4%, 24.7% 53.9%, 0% 27.9%, 11.9% 74.2%, 24.9% 54.1%, 68.6% 100%, 74.8% 41.9%)"></div>
          </div>
          <div class="flex flex-wrap items-center gap-x-4 gap-y-2">
            <p class="text-sm leading-6 text-gray-900">
              <strong class="font-semibold">GeneriCon 2023</strong><svg viewBox="0 0 2 2" class="mx-2 inline h-0.5 w-0.5 fill-current" aria-hidden="true"><circle cx="1" cy="1" r="1" /></svg>Join us in Denver from June 7 – 9 to see what's coming next.
            </p>
            <a href="#" class="flex-none rounded-full bg-gray-900 px-3.5 py-1 text-sm font-semibold text-white shadow-sm hover:bg-gray-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-gray-900">Register now <span aria-hidden="true">&rarr;</span></a>
          </div>
          <div class="flex flex-1 justify-end">
            <button type="button" class="-m-3 p-3 focus-visible:outline-offset-[-4px]">
              <span class="sr-only">Dismiss</span>
              <X class="h-5 w-5 text-gray-900" aria-hidden="true" />
            </button>
          </div>
        </div>
      `
    },
    {
      name: 'With link',
      html: `
        <div class="flex items-center justify-between gap-x-6 bg-gray-900 px-6 py-2.5 sm:pr-3.5 sm:pl-4">
          <p class="text-sm leading-6 text-white">
            <a href="#">
              <strong class="font-semibold">GeneriCon 2023</strong>
              <svg viewBox="0 0 2 2" class="mx-2 inline h-0.5 w-0.5 fill-current" aria-hidden="true"><circle cx="1" cy="1" r="1" /></svg>
              Join us in Denver from June 7 – 9 to see what's coming next
              <span aria-hidden="true">&rarr;</span>
            </a>
          </p>
          <button type="button" class="-m-3 flex-none p-3 focus-visible:outline-offset-[-4px]">
            <span class="sr-only">Dismiss</span>
            <X class="h-5 w-5 text-white" aria-hidden="true" />
          </button>
        </div>
      `
    },
    {
      name: 'Left-aligned',
      html: `
        <div class="flex items-center gap-x-6 bg-indigo-600 px-6 py-2.5 sm:px-3.5 sm:before:flex-1">
          <p class="text-sm leading-6 text-white">
            <strong class="font-semibold">GeneriCon 2023</strong><svg viewBox="0 0 2 2" class="mx-2 inline h-0.5 w-0.5 fill-current" aria-hidden="true"><circle cx="1" cy="1" r="1" /></svg>Join us in Denver from June 7 – 9 to see what's coming next.
          </p>
          <div class="flex flex-1 justify-end">
            <button type="button" class="-m-3 p-3 focus-visible:outline-offset-[-4px]">
              <span class="sr-only">Dismiss</span>
              <X class="h-5 w-5 text-white" aria-hidden="true" />
            </button>
          </div>
        </div>
      `
    },
    {
    name: 'Bottom aligned',
    html: `
    <div class="relative h-64 overflow-hidden">
      <!-- Placeholder content -->
      <div class="h-full bg-gray-100 flex items-center justify-center text-gray-400">
        Page content
      </div>
      <!-- Banner -->
      <div class="absolute inset-x-0 bottom-0 sm:flex sm:justify-center sm:px-6 sm:pb-5 lg:px-8">
        <div class="pointer-events-auto flex items-center justify-between gap-x-6 bg-gray-900 px-6 py-2.5 sm:rounded-xl sm:py-3 sm:pl-4 sm:pr-3.5">
          <p class="text-sm leading-6 text-white">
            <strong class="font-semibold">GeneriCon 2023</strong><svg viewBox="0 0 2 2" class="mx-2 inline h-0.5 w-0.5 fill-current" aria-hidden="true"><circle cx="1" cy="1" r="1" /></svg>Join us in Denver from June 7 – 9 to see what's coming next.
          </p>
          <a href="#" class="flex-none rounded-full bg-white px-3.5 py-1 text-sm font-semibold text-gray-900 shadow-sm hover:bg-gray-100 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-white">Register now <span aria-hidden="true">&rarr;</span></a>
        </div>
      </div>
    </div>
  `
  },
    {
      name: 'Floating at bottom',
      html: `
        <!-- Note: Using relative positioning for preview. Use fixed positioning in production. -->
        <div class="pointer-events-none relative inset-x-0 bottom-0 sm:flex sm:justify-center sm:px-6 sm:pb-5 lg:px-8">
          <div class="pointer-events-auto flex items-center justify-between gap-x-6 bg-gray-900 px-6 py-2.5 sm:rounded-xl sm:py-3 sm:pl-4 sm:pr-3.5">
            <p class="text-sm leading-6 text-white">
              <strong class="font-semibold">GeneriCon 2023</strong><svg viewBox="0 0 2 2" class="mx-2 inline h-0.5 w-0.5 fill-current" aria-hidden="true"><circle cx="1" cy="1" r="1" /></svg>Join us in Denver from June 7 – 9 to see what's coming next.
            </p>
            <a href="#" class="flex-none rounded-full bg-white px-3.5 py-1 text-sm font-semibold text-gray-900 shadow-sm hover:bg-gray-100 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-white">Register now <span aria-hidden="true">&rarr;</span></a>
          </div>
        </div>
      `
    },
    {
      name: 'Floating at bottom centered',
      html: `
        <!-- Note: Using relative positioning for preview. Use fixed positioning in production. -->
        <div class="pointer-events-none relative inset-x-0 bottom-0 sm:flex sm:justify-center sm:px-6 sm:pb-5 lg:px-8">
          <div class="pointer-events-auto flex items-center justify-between gap-x-6 bg-gray-900 px-6 py-2.5 sm:rounded-xl sm:py-3 sm:pl-4 sm:pr-3.5">
            <p class="text-sm leading-6 text-white">
              <strong class="font-semibold">GeneriCon 2023</strong><svg viewBox="0 0 2 2" class="mx-2 inline h-0.5 w-0.5 fill-current" aria-hidden="true"><circle cx="1" cy="1" r="1" /></svg>Join us in Denver from June 7 – 9 to see what's coming next.
            </p>
            <a href="#" class="flex-none rounded-full bg-white px-3.5 py-1 text-sm font-semibold text-gray-900 shadow-sm hover:bg-gray-100 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-white">Register now <span aria-hidden="true">&rarr;</span></a>
          </div>
        </div>
      `
    },
    {
      name: 'Privacy notice right-aligned',
      html: `
        <!-- Note: Using relative positioning for preview. Use fixed positioning in production. -->
        <div class="pointer-events-none relative inset-x-0 bottom-0 px-6 pb-6">
          <div class="pointer-events-auto ml-auto max-w-xl rounded-xl bg-white p-6 shadow-lg ring-1 ring-gray-900/10">
            <p class="text-sm leading-6 text-gray-900">
              This website uses cookies to supplement a balanced diet and provide a much deserved reward to the hardworking developers who made this site.
            </p>
            <div class="mt-4 flex items-center gap-x-5">
              <button type="button" class="rounded-md bg-gray-900 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-gray-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-gray-900">Accept all</button>
              <button type="button" class="text-sm font-semibold leading-6 text-gray-900">Reject all</button>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'Privacy notice centered',
      html: `
        <!-- Note: Using relative positioning for preview. Use fixed positioning in production. -->
        <div class="pointer-events-none relative inset-x-0 bottom-0 px-6 pb-6">
          <div class="pointer-events-auto mx-auto max-w-2xl rounded-xl bg-white p-6 shadow-lg ring-1 ring-gray-900/10">
            <p class="text-sm leading-6 text-gray-900">
              This website uses cookies to supplement a balanced diet and provide a much deserved reward to the hardworking developers who made this site.
            </p>
            <div class="mt-4 flex items-center gap-x-5">
              <button type="button" class="rounded-md bg-gray-900 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-gray-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-gray-900">Accept all</button>
              <button type="button" class="text-sm font-semibold leading-6 text-gray-900">Reject all</button>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'Privacy notice left-aligned',
      html: `
        <!-- Note: Using relative positioning for preview. Use fixed positioning in production. -->
        <div class="pointer-events-none relative inset-x-0 bottom-0 px-6 pb-6">
          <div class="pointer-events-auto max-w-xl rounded-xl bg-white p-6 shadow-lg ring-1 ring-gray-900/10">
            <p class="text-sm leading-6 text-gray-900">
              This website uses cookies to supplement a balanced diet and provide a much deserved reward to the hardworking developers who made this site.
            </p>
            <div class="mt-4 flex items-center gap-x-5">
              <button type="button" class="rounded-md bg-gray-900 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-gray-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-gray-900">Accept all</button>
              <button type="button" class="text-sm font-semibold leading-6 text-gray-900">Reject all</button>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'Privacy notice full width',
      html: `
        <div class="pointer-events-none relative inset-x-0 bottom-0 px-6 pb-6">
    <div class="pointer-events-auto mx-auto max-w-7xl rounded-xl bg-white p-6 shadow-lg ring-1 ring-gray-900/10">
      <div class="flex items-center gap-x-4 justify-between">
        <div class="flex-1">
          <p class="text-sm leading-6 text-gray-900">
            <strong class="font-semibold">Privacy Notice</strong><svg viewBox="0 0 2 2" class="mx-2 inline h-0.5 w-0.5 fill-current" aria-hidden="true"><circle cx="1" cy="1" r="1" /></svg>This website uses cookies to supplement a balanced diet and provide a much deserved reward to the hardworking developers who made this site.
          </p>
        </div>
        <div class="flex items-center gap-x-5 shrink-0">
          <button type="button" class="flex items-center justify-center rounded-md bg-gray-900 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-gray-700 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-gray-900">Accept all</button>
          <button type="button" class="text-sm font-semibold leading-6 text-gray-900">Reject all</button>
        </div>
      </div>
    </div>
  </div>
      `
    }
  ]
  
  const toggleCode = (index) => {
    showCode.value[index] = !showCode.value[index]
  }
  </script>
  
  <style scoped>
  /* Add any additional styles here if needed */
  </style>