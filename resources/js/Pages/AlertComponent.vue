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
      name: 'Alert with description',
      html: `
        <div class="bg-blue-100 border-l-4 border-blue-500 text-blue-700 p-4" role="alert">
          <p class="font-bold">Information</p>
          <p>This is an informational alert with a description. It provides additional context to the user.</p>
        </div>
      `
    },
    {
      name: 'Alert with list',
      html: `
        <div class="bg-yellow-100 border-l-4 border-yellow-500 text-yellow-700 p-4" role="alert">
          <p class="font-bold">Warning</p>
          <ul class="list-disc list-inside">
            <li>This is the first warning item</li>
            <li>This is the second warning item</li>
            <li>This is the third warning item</li>
          </ul>
        </div>
      `
    },
    {
      name: 'Alert with actions',
      html: `
        <div class="bg-green-100 border-l-4 border-green-500 text-green-700 p-4" role="alert">
          <p class="font-bold">Success</p>
          <p>Your action was completed successfully.</p>
          <div class="mt-3">
            <button class="bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded mr-2">
              View Result
            </button>
            <button class="bg-green-200 hover:bg-green-300 text-green-800 font-bold py-2 px-4 rounded">
              Dismiss
            </button>
          </div>
        </div>
      `
    },
    {
      name: 'Alert with link on right',
      html: `
        <div class="bg-purple-100 border-l-4 border-purple-500 text-purple-700 p-4 flex justify-between items-center" role="alert">
          <div>
            <p class="font-bold">Notification</p>
            <p>You have a new message in your inbox.</p>
          </div>
          <a href="#" class="underline text-purple-600 hover:text-purple-800">View message</a>
        </div>
      `
    },
    {
      name: 'Alert with accent border',
      html: `
        <div class="bg-red-100 border-t-4 border-red-500 rounded-b text-red-700 px-4 py-3 shadow-md" role="alert">
          <div class="flex">
            <div class="py-1"><svg class="fill-current h-6 w-6 text-red-500 mr-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M2.93 17.07A10 10 0 1 1 17.07 2.93 10 10 0 0 1 2.93 17.07zm12.73-1.41A8 8 0 1 0 4.34 4.34a8 8 0 0 0 11.32 11.32zM9 11V9h2v6H9v-4zm0-6h2v2H9V5z"/></svg></div>
            <div>
              <p class="font-bold">Error</p>
              <p class="text-sm">Something went wrong. Please try again later.</p>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'Alert with dismiss button',
      html: `
        <div class="bg-indigo-100 border-l-4 border-indigo-500 text-indigo-700 p-4" role="alert">
          <div class="flex justify-between items-center">
            <div>
              <p class="font-bold">Dismissible Alert</p>
              <p>This alert can be dismissed by clicking the close button.</p>
            </div>
            <button class="text-indigo-700 hover:text-indigo-900" aria-label="Close">
              <svg class="h-6 w-6 fill-current" role="button" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><title>Close</title><path d="M14.348 14.849a1.2 1.2 0 0 1-1.697 0L10 11.819l-2.651 3.029a1.2 1.2 0 1 1-1.697-1.697l2.758-3.15-2.759-3.152a1.2 1.2 0 1 1 1.697-1.697L10 8.183l2.651-3.031a1.2 1.2 0 1 1 1.697 1.697l-2.758 3.152 2.758 3.15a1.2 1.2 0 0 1 0 1.698z"/></svg>
            </button>
          </div>
        </div>
      `
    }
  ]
  
  const toggleCode = (index) => {
    showCode.value[index] = !showCode.value[index]
  }
  </script>