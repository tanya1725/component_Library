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
  import { Bell, ArrowRight, ChevronRight } from 'lucide-vue-next'
  
  const showCode = ref({})
  
  const variations = [
    {
      name: 'Simple',
      html: `
        <div class="rounded-md bg-blue-50 p-4">
          <div class="flex">
            <div class="flex-shrink-0">
              <Bell class="h-5 w-5 text-blue-400" aria-hidden="true" />
            </div>
            <div class="ml-3">
              <h3 class="text-sm font-medium text-blue-800">Information</h3>
              <div class="mt-2 text-sm text-blue-700">
                <p>This is a simple action panel with some important information.</p>
              </div>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'With link',
      html: `
        <div class="rounded-md bg-blue-50 p-4">
          <div class="flex">
            <div class="flex-shrink-0">
              <Bell class="h-5 w-5 text-blue-400" aria-hidden="true" />
            </div>
            <div class="ml-3">
              <h3 class="text-sm font-medium text-blue-800">Information</h3>
              <div class="mt-2 text-sm text-blue-700">
                <p>This action panel includes a link for more information.</p>
              </div>
              <div class="mt-4">
                <a href="#" class="text-sm font-medium text-blue-600 hover:text-blue-500">
                  Learn more
                  <ArrowRight class="inline-block w-4 h-4 ml-1" aria-hidden="true" />
                </a>
              </div>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'With button on right',
      html: `
        <div class="rounded-md bg-yellow-50 p-4">
          <div class="flex">
            <div class="flex-shrink-0">
              <Bell class="h-5 w-5 text-yellow-400" aria-hidden="true" />
            </div>
            <div class="ml-3 flex-grow">
              <h3 class="text-sm font-medium text-yellow-800">Attention needed</h3>
              <div class="mt-2 text-sm text-yellow-700">
                <p>This action panel includes a button on the right side.</p>
              </div>
            </div>
            <div class="ml-auto pl-3">
              <div class="-mx-1.5 -my-1.5">
                <button type="button" class="inline-flex rounded-md bg-yellow-50 p-1.5 text-yellow-500 hover:bg-yellow-100 focus:outline-none focus:ring-2 focus:ring-yellow-600 focus:ring-offset-2 focus:ring-offset-yellow-50">
                  Take action
                </button>
              </div>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'With button at top right',
      html: `
        <div class="rounded-md bg-green-50 p-4">
          <div class="flex justify-between">
            <div class="flex">
              <div class="flex-shrink-0">
                <Bell class="h-5 w-5 text-green-400" aria-hidden="true" />
              </div>
              <div class="ml-3">
                <h3 class="text-sm font-medium text-green-800">Success</h3>
                <div class="mt-2 text-sm text-green-700">
                  <p>This action panel has a button at the top right corner.</p>
                </div>
              </div>
            </div>
            <div>
              <button type="button" class="inline-flex rounded-md bg-green-50 p-1.5 text-green-500 hover:bg-green-100 focus:outline-none focus:ring-2 focus:ring-green-600 focus:ring-offset-2 focus:ring-offset-green-50">
                <span class="sr-only">Dismiss</span>
                <ChevronRight class="h-5 w-5" aria-hidden="true" />
              </button>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'With toggle',
      html: `
        <div class="rounded-md bg-purple-50 p-4">
          <div class="flex items-start">
            <div class="flex-1 min-w-0">
              <h3 class="text-sm font-medium text-purple-800">Notifications</h3>
              <p class="mt-1 text-sm text-purple-700">
                Receive notifications for important updates and events.
              </p>
            </div>
            <div class="ml-4 flex-shrink-0">
              <button type="button" class="bg-purple-200 relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-offset-2" role="switch" aria-checked="true">
                <span aria-hidden="true" class="translate-x-5 pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out"></span>
              </button>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'With input',
      html: `
        <div class="rounded-md bg-gray-50 p-4">
          <h3 class="text-sm font-medium text-gray-800 mb-2">Subscribe to our newsletter</h3>
          <form class="mt-2 sm:flex sm:items-center">
            <label for="email" class="sr-only">Email</label>
            <input
              type="email"
              name="email"
              id="email"
              class="w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm placeholder-gray-400 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
              placeholder="Enter your email"
            />
            <button
              type="submit"
              class="mt-3 w-full px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:flex-shrink-0"
            >
              Subscribe
            </button>
          </form>
        </div>
      `
    },
    {
      name: 'Simple well',
      html: `
        <div class="rounded-md bg-gray-100 p-4">
          <div class="flex">
            <div class="flex-shrink-0">
              <Bell class="h-5 w-5 text-gray-400" aria-hidden="true" />
            </div>
            <div class="ml-3">
              <h3 class="text-sm font-medium text-gray-800">Information</h3>
              <div class="mt-2 text-sm text-gray-700">
                <p>This is a simple well panel with some important information.</p>
              </div>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'With well',
      html: `
        <div class="rounded-md bg-white p-4 border border-gray-200">
          <h3 class="text-lg font-medium text-gray-900 mb-2">Account Status</h3>
          <div class="rounded-md bg-gray-100 p-4 mt-2">
            <p class="text-sm text-gray-700">
              Your account is currently active and in good standing.
            </p>
          </div>
          <div class="mt-4 flex justify-end">
            <button type="button" class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
              View Details
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