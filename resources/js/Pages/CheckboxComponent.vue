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
      name: 'List with description',
      html: `
        <fieldset>
          <legend class="text-base font-semibold text-gray-900">Notifications</legend>
          <div class="mt-4 space-y-4">
            <div class="relative flex items-start">
              <div class="flex h-6 items-center">
                <input id="comments" name="comments" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
              </div>
              <div class="ml-3 text-sm leading-6">
                <label for="comments" class="font-medium text-gray-900">Comments</label>
                <p class="text-gray-500">Get notified when someones posts a comment on a posting.</p>
              </div>
            </div>
            <div class="relative flex items-start">
              <div class="flex h-6 items-center">
                <input id="candidates" name="candidates" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
              </div>
              <div class="ml-3 text-sm leading-6">
                <label for="candidates" class="font-medium text-gray-900">Candidates</label>
                <p class="text-gray-500">Get notified when a candidate applies for a job.</p>
              </div>
            </div>
            <div class="relative flex items-start">
              <div class="flex h-6 items-center">
                <input id="offers" name="offers" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
              </div>
              <div class="ml-3 text-sm leading-6">
                <label for="offers" class="font-medium text-gray-900">Offers</label>
                <p class="text-gray-500">Get notified when a candidate accepts or rejects an offer.</p>
              </div>
            </div>
          </div>
        </fieldset>
      `
    },
    {
      name: 'List with inline description',
      html: `
        <fieldset>
          <legend class="text-base font-semibold text-gray-900">Notifications</legend>
          <div class="mt-4 space-y-4">
            <div class="flex items-center">
              <input id="push-everything" name="push-notifications" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
              <label for="push-everything" class="ml-3 block text-sm font-medium leading-6 text-gray-900">
                Everything
              </label>
            </div>
            <div class="flex items-center">
              <input id="push-email" name="push-notifications" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
              <label for="push-email" class="ml-3 block text-sm font-medium leading-6 text-gray-900">
                Same as email
              </label>
            </div>
            <div class="flex items-center">
              <input id="push-nothing" name="push-notifications" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
              <label for="push-nothing" class="ml-3 block text-sm font-medium leading-6 text-gray-900">
                No push notifications
              </label>
            </div>
          </div>
        </fieldset>
      `
    },
    {
      name: 'List with checkbox on right',
      html: `
        <fieldset>
          <legend class="text-base font-semibold text-gray-900">Privacy settings</legend>
          <div class="mt-4 space-y-4">
            <div class="flex items-center justify-between">
              <label for="comments" class="text-sm font-medium leading-6 text-gray-900">Comments</label>
              <input id="comments" name="comments" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
            </div>
            <div class="flex items-center justify-between">
              <label for="candidates" class="text-sm font-medium leading-6 text-gray-900">Candidates</label>
              <input id="candidates" name="candidates" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
            </div>
            <div class="flex items-center justify-between">
              <label for="offers" class="text-sm font-medium leading-6 text-gray-900">Offers</label>
              <input id="offers" name="offers" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
            </div>
          </div>
        </fieldset>
      `
    },
    {
      name: 'Simple list with heading',
      html: `
        <fieldset>
          <legend class="text-sm font-semibold leading-6 text-gray-900">By Email</legend>
          <div class="mt-4 space-y-4">
            <div class="relative flex items-start">
              <div class="flex h-6 items-center">
                <input id="comments" name="comments" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
              </div>
              <div class="ml-3 text-sm leading-6">
                <label for="comments" class="font-medium text-gray-900">Comments</label>
              </div>
            </div>
            <div class="relative flex items-start">
              <div class="flex h-6 items-center">
                <input id="candidates" name="candidates" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
              </div>
              <div class="ml-3 text-sm leading-6">
                <label for="candidates" class="font-medium text-gray-900">Candidates</label>
              </div>
            </div>
            <div class="relative flex items-start">
              <div class="flex h-6 items-center">
                <input id="offers" name="offers" type="checkbox" class="h-4 w-4 rounded border-gray-300 text-indigo-600 focus:ring-indigo-600">
              </div>
              <div class="ml-3 text-sm leading-6">
                <label for="offers" class="font-medium text-gray-900">Offers</label>
              </div>
            </div>
          </div>
        </fieldset>
      `
    }
  ]
  
  const toggleCode = (index) => {
    showCode.value[index] = !showCode.value[index]
  }
  </script>