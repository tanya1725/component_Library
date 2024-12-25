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
  
  const showCode = ref({})
  
  const variations = [
    {
      name: 'With border',
      html: `
        <span class="inline-flex items-center rounded-md bg-gray-50 px-2 py-1 text-xs font-medium text-gray-600 ring-1 ring-inset ring-gray-500/10">
          Badge
        </span>
      `
    },
    {
      name: 'With border on dark',
      html: `
        <span class="inline-flex items-center rounded-md bg-gray-400/10 px-2 py-1 text-xs font-medium text-gray-400 ring-1 ring-inset ring-gray-400/20">
          Badge
        </span>
      `
    },
    {
      name: 'With border and dot',
      html: `
        <span class="inline-flex items-center rounded-md bg-gray-50 px-2 py-1 text-xs font-medium text-gray-600 ring-1 ring-inset ring-gray-500/10">
          <svg class="mr-1.5 h-2 w-2 fill-gray-400" viewBox="0 0 6 6" aria-hidden="true">
            <circle cx="3" cy="3" r="3" />
          </svg>
          Badge
        </span>
      `
    },
    {
      name: 'With border and dot on dark',
      html: `
        <span class="inline-flex items-center rounded-md bg-gray-400/10 px-2 py-1 text-xs font-medium text-gray-400 ring-1 ring-inset ring-gray-400/20">
          <svg class="mr-1.5 h-2 w-2 fill-gray-400" viewBox="0 0 6 6" aria-hidden="true">
            <circle cx="3" cy="3" r="3" />
          </svg>
          Badge
        </span>
      `
    },
    {
      name: 'Pill with border',
      html: `
        <span class="inline-flex items-center rounded-full bg-gray-50 px-2 py-1 text-xs font-medium text-gray-600 ring-1 ring-inset ring-gray-500/10">
          Badge
        </span>
      `
    },
    {
      name: 'Pill with border and dot',
      html: `
        <span class="inline-flex items-center rounded-full bg-gray-50 px-2 py-1 text-xs font-medium text-gray-600 ring-1 ring-inset ring-gray-500/10">
          <svg class="mr-1.5 h-2 w-2 fill-gray-400" viewBox="0 0 6 6" aria-hidden="true">
            <circle cx="3" cy="3" r="3" />
          </svg>
          Badge
        </span>
      `
    },
    {
      name: 'With border and remove button',
      html: `
        <span class="inline-flex items-center gap-x-0.5 rounded-md bg-gray-50 px-2 py-1 text-xs font-medium text-gray-600 ring-1 ring-inset ring-gray-500/10">
          Badge
          <button type="button" class="group relative -mr-1 h-3.5 w-3.5 rounded-sm hover:bg-gray-500/20">
            <span class="sr-only">Remove</span>
            <svg viewBox="0 0 14 14" class="h-3.5 w-3.5 stroke-gray-600/50 group-hover:stroke-gray-600/75">
              <path d="M4 4l6 6m0-6l-6 6" />
            </svg>
            <span class="absolute -inset-1"></span>
          </button>
        </span>
      `
    },
    {
      name: 'Flat',
      html: `
        <span class="inline-flex items-center rounded-md bg-gray-100 px-2 py-1 text-xs font-medium text-gray-600">
          Badge
        </span>
      `
    },
    {
      name: 'Flat pill',
      html: `
        <span class="inline-flex items-center rounded-full bg-gray-100 px-2 py-1 text-xs font-medium text-gray-600">
          Badge
        </span>
      `
    },
    {
      name: 'Flat with dot',
      html: `
        <span class="inline-flex items-center rounded-md bg-gray-100 px-2 py-1 text-xs font-medium text-gray-600">
          <svg class="mr-1.5 h-2 w-2 fill-gray-400" viewBox="0 0 6 6" aria-hidden="true">
            <circle cx="3" cy="3" r="3" />
          </svg>
          Badge
        </span>
      `
    },
    {
      name: 'Flat pill with dot',
      html: `
        <span class="inline-flex items-center rounded-full bg-gray-100 px-2 py-1 text-xs font-medium text-gray-600">
          <svg class="mr-1.5 h-2 w-2 fill-gray-400" viewBox="0 0 6 6" aria-hidden="true">
            <circle cx="3" cy="3" r="3" />
          </svg>
          Badge
        </span>
      `
    },
    {
      name: 'Flat with remove button',
      html: `
        <span class="inline-flex items-center gap-x-0.5 rounded-md bg-gray-100 px-2 py-1 text-xs font-medium text-gray-600">
          Badge
          <button type="button" class="group relative -mr-1 h-3.5 w-3.5 rounded-sm hover:bg-gray-200">
            <span class="sr-only">Remove</span>
            <svg viewBox="0 0 14 14" class="h-3.5 w-3.5 stroke-gray-600/50 group-hover:stroke-gray-600/75">
              <path d="M4 4l6 6m0-6l-6 6" />
            </svg>
            <span class="absolute -inset-1"></span>
          </button>
        </span>
      `
    },
    {
      name: 'Small with border',
      html: `
        <span class="inline-flex items-center rounded-md bg-gray-50 px-1.5 py-0.5 text-xs font-medium text-gray-600 ring-1 ring-inset ring-gray-500/10">
          Badge
        </span>
      `
    },
    {
      name: 'Small flat',
      html: `
        <span class="inline-flex items-center rounded-md bg-gray-100 px-1.5 py-0.5 text-xs font-medium text-gray-600">
          Badge
        </span>
      `
    },
    {
      name: 'Small pill with border',
      html: `
        <span class="inline-flex items-center rounded-full bg-gray-50 px-1.5 py-0.5 text-xs font-medium text-gray-600 ring-1 ring-inset ring-gray-500/10">
          Badge
        </span>
      `
    },
    {
      name: 'Small flat pill',
      html: `
        <span class="inline-flex items-center rounded-full bg-gray-100 px-1.5 py-0.5 text-xs font-medium text-gray-600">
          Badge
        </span>
      `
    },
    {
      name: 'Small flat with dot',
      html: `
        <span class="inline-flex items-center rounded-md bg-gray-100 px-1.5 py-0.5 text-xs font-medium text-gray-600">
          <svg class="mr-1 h-1.5 w-1.5 fill-gray-400" viewBox="0 0 6 6" aria-hidden="true">
            <circle cx="3" cy="3" r="3" />
          </svg>
          Badge
        </span>
      `
    },
    {
      name: 'Small flat pill with dot',
      html: `
        <span class="inline-flex items-center rounded-full bg-gray-100 px-1.5 py-0.5 text-xs font-medium text-gray-600">
          <svg class="mr-1 h-1.5 w-1.5 fill-gray-400" viewBox="0 0 6 6" aria-hidden="true">
            <circle cx="3" cy="3" r="3" />
          </svg>
          Badge
        </span>
      `
    }
  ]
  
  const toggleCode = (index) => {
    showCode.value[index] = !showCode.value[index]
  }
  </script>
  
  