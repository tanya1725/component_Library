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
      name: 'Avatar group stacked bottom to top',
      html: `
        <div class="flex -space-x-2 overflow-hidden">
          <img class="inline-block h-8 w-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="User 1">
          <img class="inline-block h-8 w-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="User 2">
          <img class="inline-block h-8 w-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.25&w=256&h=256&q=80" alt="User 3">
          <img class="inline-block h-8 w-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="User 4">
        </div>
      `
    },
    {
      name: 'Circular avatars',
      html: `
        <div class="flex space-x-4">
          <img class="h-12 w-12 rounded-full object-cover" src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Circular avatar 1">
          <img class="h-10 w-10 rounded-full object-cover" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Circular avatar 2">
          <img class="h-8 w-8 rounded-full object-cover" src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.25&w=256&h=256&q=80" alt="Circular avatar 3">
        </div>
      `
    },
    {
      name: 'Rounded avatars',
      html: `
        <div class="flex space-x-4">
          <img class="h-12 w-12 rounded object-cover" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Rounded avatar 1">
          <img class="h-10 w-10 rounded object-cover" src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Rounded avatar 2">
          <img class="h-8 w-8 rounded object-cover" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Rounded avatar 3">
        </div>
      `
    },
    {
      name: 'Circular avatars with top notification',
      html: `
        <div class="flex space-x-4">
          <span class="relative inline-block">
            <img class="h-12 w-12 rounded-full object-cover" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Circular avatar with notification 1">
            <span class="absolute top-0 right-0 block h-3 w-3 rounded-full ring-2 ring-white bg-red-400"></span>
          </span>
          <span class="relative inline-block">
            <img class="h-10 w-10 rounded-full object-cover" src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Circular avatar with notification 2">
            <span class="absolute top-0 right-0 block h-2.5 w-2.5 rounded-full ring-2 ring-white bg-green-400"></span>
          </span>
          <span class="relative inline-block">
            <img class="h-8 w-8 rounded-full object-cover" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Circular avatar with notification 3">
            <span class="absolute top-0 right-0 block h-2 w-2 rounded-full ring-2 ring-white bg-blue-400"></span>
          </span>
        </div>
      `
    },
    {
      name: 'Rounded avatars with top notification',
      html: `
        <div class="flex space-x-4">
          <span class="relative inline-block">
            <img class="h-12 w-12 rounded object-cover" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Rounded avatar with notification 1">
            <span class="absolute top-0 right-0 block h-3 w-3 rounded-full ring-2 ring-white bg-red-400"></span>
          </span>
          <span class="relative inline-block">
            <img class="h-10 w-10 rounded object-cover" src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Rounded avatar with notification 2">
            <span class="absolute top-0 right-0 block h-2.5 w-2.5 rounded-full ring-2 ring-white bg-green-400"></span>
          </span>
          <span class="relative inline-block">
            <img class="h-8 w-8 rounded object-cover" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Rounded avatar with notification 3">
            <span class="absolute top-0 right-0 block h-2 w-2 rounded-full ring-2 ring-white bg-blue-400"></span>
          </span>
        </div>
      `
    },
    {
      name: 'Circular avatars with bottom notification',
      html: `
        <div class="flex space-x-4">
          <span class="relative inline-block">
            <img class="h-12 w-12 rounded-full object-cover" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Circular avatar with bottom notification 1">
            <span class="absolute bottom-0 right-0 block h-3 w-3 rounded-full ring-2 ring-white bg-red-400"></span>
          </span>
          <span class="relative inline-block">
            <img class="h-10 w-10 rounded-full object-cover" src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Circular avatar with bottom notification 2">
            <span class="absolute bottom-0 right-0 block h-2.5 w-2.5 rounded-full ring-2 ring-white bg-green-400"></span>
          </span>
          <span class="relative inline-block">
            <img class="h-8 w-8 rounded-full object-cover" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Circular avatar with bottom notification 3">
            <span class="absolute bottom-0 right-0 block h-2 w-2 rounded-full ring-2 ring-white bg-blue-400"></span>
          </span>
        </div>
      `
    },
    {
      name: 'Rounded avatars with bottom notification',
      html: `
        <div class="flex space-x-4">
          <span class="relative inline-block">
            <img class="h-12 w-12 rounded object-cover" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Rounded avatar with bottom notification 1">
            <span class="absolute bottom-0 right-0 block h-3 w-3 rounded-full ring-2 ring-white bg-red-400"></span>
          </span>
          <span class="relative inline-block">
            <img class="h-10 w-10 rounded object-cover" src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Rounded avatar with bottom notification 2">
            <span class="absolute bottom-0 right-0 block h-2.5 w-2.5 rounded-full ring-2 ring-white bg-green-400"></span>
          </span>
          <span class="relative inline-block">
            <img class="h-8 w-8 rounded object-cover" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Rounded avatar with bottom notification 3">
            <span class="absolute bottom-0 right-0 block h-2 w-2 rounded-full ring-white bg-blue-400"></span>
          </span>
        </div>
      `
    },
    {
      name: 'Circular avatars with placeholder icon',
      html: `
        <div class="flex space-x-4">
          <span class="inline-block h-12 w-12 rounded-full overflow-hidden bg-gray-100">
            <svg class="h-full w-full text-gray-300" fill="currentColor" viewBox="0 0 24 24">
              <path d="M24 20.993V24H0v-2.996A14.977 14.977 0 0112.004 15c4.904 0 9.26 2.354 11.996 5.993zM16.002 8.999a4 4 0 11-8 0 4 4 0 018 0z" />
            </svg>
          </span>
          <span class="inline-block h-10 w-10 rounded-full overflow-hidden bg-gray-100">
            <svg class="h-full w-full text-gray-300" fill="currentColor" viewBox="0 0 24 24">
              <path d="M24 20.993V24H0v-2.996A14.977 14.977 0 0112.004 15c4.904 0 9.26 2.354 11.996 5.993zM16.002 8.999a4 4 0 11-8 0 4 4 0 018 0z" />
            </svg>
          </span>
          <span class="inline-block h-8 w-8 rounded-full overflow-hidden bg-gray-100">
            <svg class="h-full w-full text-gray-300" fill="currentColor" viewBox="0 0 24 24">
              <path d="M24 20.993V24H0v-2.996A14.977 14.977 0 0112.004 15c4.904 0 9.26 2.354 11.996 5.993zM16.002 8.999a4 4 0 11-8 0 4 4 0 018 0z" />
            </svg>
          </span>
        </div>
      `
    },
    {
      name: 'Circular avatars with placeholder initials',
      html: `
        <div class="flex space-x-4">
          <span class="inline-flex items-center justify-center h-12 w-12 rounded-full bg-gray-500">
            <span class="text-xl font-medium leading-none text-white">JD</span>
          </span>
          <span class="inline-flex items-center justify-center h-10 w-10 rounded-full bg-gray-500">
            <span class="text-lg font-medium leading-none text-white">AB</span>
          </span>
          <span class="inline-flex items-center justify-center h-8 w-8 rounded-full bg-gray-500">
            <span class="text-sm font-medium leading-none text-white">CD</span>
          </span>
        </div>
      `
    },
    {
      name: 'Avatar group stacked top to bottom',
      html: `
        <div class="flex flex-col items-center -space-y-1">
          <img class="inline-block h-8 w-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="User 1">
          <img class="inline-block h-8 w-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="User 2">
          <img class="inline-block h-8 w-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2.25&w=256&h=256&q=80" alt="User 3">
          <img class="inline-block h-8 w-8 rounded-full ring-2 ring-white" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="User 4">
        </div>
      `
    },
    {
      name: 'Avatar with text',
      html: `
        <div class="flex items-center space-x-4">
          <img class="h-12 w-12 rounded-full object-cover" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="Avatar with text">
          <div class="space-y-1">
            <div class="font-medium">John Doe</div>
            <div class="text-sm text-gray-500">john.doe@example.com</div>
          </div>
        </div>
      `
    }
  ]
  
  const toggleCode = (index) => {
    showCode.value[index] = !showCode.value[index]
  }
  </script>
  
  