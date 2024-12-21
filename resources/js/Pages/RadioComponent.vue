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
    name: 'Simple list',
    html: `
      <div class="space-y-2">
        <label class="flex items-center">
          <input type="radio" name="simple-list" value="option1" class="form-radio h-4 w-4 text-blue-600">
          <span class="ml-2 text-gray-700">Option 1</span>
        </label>
        <label class="flex items-center">
          <input type="radio" name="simple-list" value="option2" class="form-radio h-4 w-4 text-blue-600">
          <span class="ml-2 text-gray-700">Option 2</span>
        </label>
        <label class="flex items-center">
          <input type="radio" name="simple-list" value="option3" class="form-radio h-4 w-4 text-blue-600">
          <span class="ml-2 text-gray-700">Option 3</span>
        </label>
      </div>
    `
  },
  {
    name: 'Simple inline list',
    html: `
      <div class="flex space-x-4">
        <label class="flex items-center">
          <input type="radio" name="inline-list" value="option1" class="form-radio h-4 w-4 text-blue-600">
          <span class="ml-2 text-gray-700">Option 1</span>
        </label>
        <label class="flex items-center">
          <input type="radio" name="inline-list" value="option2" class="form-radio h-4 w-4 text-blue-600">
          <span class="ml-2 text-gray-700">Option 2</span>
        </label>
        <label class="flex items-center">
          <input type="radio" name="inline-list" value="option3" class="form-radio h-4 w-4 text-blue-600">
          <span class="ml-2 text-gray-700">Option 3</span>
        </label>
      </div>
    `
  },
  {
    name: 'List with description',
    html: `
      <div class="space-y-2">
        <label class="flex items-start">
          <input type="radio" name="list-with-description" value="option1" class="form-radio h-4 w-4 text-blue-600 mt-1">
          <div class="ml-2">
            <span class="text-gray-700 font-medium">Option 1</span>
            <p class="text-gray-500 text-sm">This is a description for Option 1</p>
          </div>
        </label>
        <label class="flex items-start">
          <input type="radio" name="list-with-description" value="option2" class="form-radio h-4 w-4 text-blue-600 mt-1">
          <div class="ml-2">
            <span class="text-gray-700 font-medium">Option 2</span>
            <p class="text-gray-500 text-sm">This is a description for Option 2</p>
          </div>
        </label>
        <label class="flex items-start">
          <input type="radio" name="list-with-description" value="option3" class="form-radio h-4 w-4 text-blue-600 mt-1">
          <div class="ml-2">
            <span class="text-gray-700 font-medium">Option 3</span>
            <p class="text-gray-500 text-sm">This is a description for Option 3</p>
          </div>
        </label>
      </div>
    `
  },
  {
    name: 'List with inline description',
    html: `
      <div class="space-y-2">
        <label class="flex items-center">
          <input type="radio" name="list-with-inline-description" value="option1" class="form-radio h-4 w-4 text-blue-600">
          <span class="ml-2 text-gray-700">Option 1</span>
          <span class="ml-2 text-gray-500 text-sm">- Description for Option 1</span>
        </label>
        <label class="flex items-center">
          <input type="radio" name="list-with-inline-description" value="option2" class="form-radio h-4 w-4 text-blue-600">
          <span class="ml-2 text-gray-700">Option 2</span>
          <span class="ml-2 text-gray-500 text-sm">- Description for Option 2</span>
        </label>
        <label class="flex items-center">
          <input type="radio" name="list-with-inline-description" value="option3" class="form-radio h-4 w-4 text-blue-600">
          <span class="ml-2 text-gray-700">Option 3</span>
          <span class="ml-2 text-gray-500 text-sm">- Description for Option 3</span>
        </label>
      </div>
    `
  },
  {
    name: 'List with radio on right',
    html: `
      <div class="space-y-2">
        <label class="flex items-center justify-between">
          <span class="text-gray-700">Option 1</span>
          <input type="radio" name="list-with-radio-right" value="option1" class="form-radio h-4 w-4 text-blue-600">
        </label>
        <label class="flex items-center justify-between">
          <span class="text-gray-700">Option 2</span>
          <input type="radio" name="list-with-radio-right" value="option2" class="form-radio h-4 w-4 text-blue-600">
        </label>
        <label class="flex items-center justify-between">
          <span class="text-gray-700">Option 3</span>
          <input type="radio" name="list-with-radio-right" value="option3" class="form-radio h-4 w-4 text-blue-600">
        </label>
      </div>
    `
  },
  {
    name: 'Simple list with radio on right',
    html: `
      <div class="space-y-2">
        <label class="flex items-center justify-between">
          <div>
            <span class="text-gray-700 font-medium">Option 1</span>
            <p class="text-gray-500 text-sm">Description for Option 1</p>
          </div>
          <input type="radio" name="simple-list-with-radio-right" value="option1" class="form-radio h-4 w-4 text-blue-600">
        </label>
        <label class="flex items-center justify-between">
          <div>
            <span class="text-gray-700 font-medium">Option 2</span>
            <p class="text-gray-500 text-sm">Description for Option 2</p>
          </div>
          <input type="radio" name="simple-list-with-radio-right" value="option2" class="form-radio h-4 w-4 text-blue-600">
        </label>
        <label class="flex items-center justify-between">
          <div>
            <span class="text-gray-700 font-medium">Option 3</span>
            <p class="text-gray-500 text-sm">Description for Option 3</p>
          </div>
          <input type="radio" name="simple-list-with-radio-right" value="option3" class="form-radio h-4 w-4 text-blue-600">
        </label>
      </div>
    `
  },
  {
    name: 'Simple table',
    html: `
      <table class="min-w-full divide-y divide-gray-200">
        <thead class="bg-gray-50">
          <tr>
            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Option</th>
            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Description</th>
            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Select</th>
          </tr>
        </thead>
        <tbody class="bg-white divide-y divide-gray-200">
          <tr>
            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">Option 1</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Description for Option 1</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
              <input type="radio" name="simple-table" value="option1" class="form-radio h-4 w-4 text-blue-600">
            </td>
          </tr>
          <tr>
            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">Option 2</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Description for Option 2</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
              <input type="radio" name="simple-table" value="option2" class="form-radio h-4 w-4 text-blue-600">
            </td>
          </tr>
          <tr>
            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">Option 3</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">Description for Option 3</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
              <input type="radio" name="simple-table" value="option3" class="form-radio h-4 w-4 text-blue-600">
            </td>
          </tr>
        </tbody>
      </table>
    `
  },
  {
    name: 'List with descriptions in panel',
    html: `
      <div class="bg-white shadow overflow-hidden sm:rounded-md">
        <ul class="divide-y divide-gray-200">
          <li>
            <label class="px-4 py-4 sm:px-6 flex items-start">
              <input type="radio" name="list-with-descriptions-in-panel" value="option1" class="form-radio h-4 w-4 text-blue-600 mt-1">
              <div class="ml-3">
                <p class="text-sm font-medium text-gray-900">Option 1</p>
                <p class="text-sm text-gray-500">This is a detailed description for Option 1</p>
              </div>
            </label>
          </li>
          <li>
            <label class="px-4 py-4 sm:px-6 flex items-start">
              <input type="radio" name="list-with-descriptions-in-panel" value="option2" class="form-radio h-4 w-4 text-blue-600 mt-1">
              <div class="ml-3">
                <p class="text-sm font-medium text-gray-900">Option 2</p>
                <p class="text-sm text-gray-500">This is a detailed description for Option 2</p>
              </div>
            </label>
          </li>
          <li>
            <label class="px-4 py-4 sm:px-6 flex items-start">
              <input type="radio" name="list-with-descriptions-in-panel" value="option3" class="form-radio h-4 w-4 text-blue-600 mt-1">
              <div class="ml-3">
                <p class="text-sm font-medium text-gray-900">Option 3</p>
                <p class="text-sm text-gray-500">This is a detailed description for Option 3</p>
              </div>
            </label>
          </li>
        </ul>
      </div>
    `
  },
  {
    name: 'Color picker',
    html: `
      <div class="flex space-x-3">
        <label class="flex items-center">
          <input type="radio" name="color-picker" value="red" class="sr-only">
          <span class="h-8 w-8 bg-red-500 rounded-full border-2 border-transparent flex items-center justify-center cursor-pointer focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500">
            <span class="sr-only">Red</span>
          </span>
        </label>
        <label class="flex items-center">
          <input type="radio" name="color-picker" value="green" class="sr-only">
          <span class="h-8 w-8 bg-green-500 rounded-full border-2 border-transparent flex items-center justify-center cursor-pointer focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500">
            <span class="sr-only">Green</span>
          </span>
        </label>
        <label class="flex items-center">
          <input type="radio" name="color-picker" value="blue" class="sr-only">
          <span class="h-8 w-8 bg-blue-500 rounded-full border-2 border-transparent flex items-center justify-center cursor-pointer focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
            <span class="sr-only">Blue</span>
          </span>
        </label>
      </div>
    `
  },
  {
    name: 'Cards',
    html: `
      <div class="grid grid-cols-1 gap-4 sm:grid-cols-3">
        <label class="relative bg-white border rounded-lg shadow-sm p-4 flex cursor-pointer focus:outline-none">
          <input type="radio" name="cards" value="option1" class="sr-only" aria-labelledby="option1-label" aria-describedby="option1-description">
          <div class="flex-1 flex">
            <div class="flex flex-col">
              <span id="option1-label" class="block text-sm font-medium text-gray-900">Option 1</span>
              <span id="option1-description" class="mt-1 flex items-center text-sm text-gray-500">This is the content for Option 1</span>
            </div>
          </div>
          <div class="absolute -inset-px rounded-lg border-2 pointer-events-none" aria-hidden="true"></div>
        </label>
        <label class="relative bg-white border rounded-lg shadow-sm p-4 flex cursor-pointer focus:outline-none">
          <input type="radio" name="cards" value="option2" class="sr-only" aria-labelledby="option2-label" aria-describedby="option2-description">
          <div class="flex-1 flex">
            <div class="flex flex-col">
              <span id="option2-label" class="block text-sm font-medium text-gray-900">Option 2</span>
              <span id="option2-description" class="mt-1 flex items-center text-sm text-gray-500">This is the content for Option 2</span>
            </div>
          </div>
          <div class="absolute -inset-px rounded-lg border-2 pointer-events-none" aria-hidden="true"></div>
        </label>
        <label class="relative bg-white border rounded-lg shadow-sm p-4 flex cursor-pointer focus:outline-none">
          <input type="radio" name="cards" value="option3" class="sr-only" aria-labelledby="option3-label" aria-describedby="option3-description">
          <div class="flex-1 flex">
            <div class="flex flex-col">
              <span id="option3-label" class="block text-sm font-medium text-gray-900">Option 3</span>
              <span id="option3-description" class="mt-1 flex items-center text-sm text-gray-500">This is the content for Option 3</span>
            </div>
          </div>
          <div class="absolute -inset-px rounded-lg border-2 pointer-events-none" aria-hidden="true"></div>
        </label>
      </div>
    `
  },
  {
    name: 'Small cards',
    html: `
      <div class="flex flex-wrap gap-4">
        <label class="relative bg-white border rounded-md px-3 py-2 flex items-center cursor-pointer focus:outline-none">
          <input type="radio" name="small-cards" value="option1" class="sr-only" aria-labelledby="small-option1-label">
          <span id="small-option1-label" class="block text-sm font-medium text-gray-900">S</span>
          <div class="absolute -inset-px rounded-md border-2 pointer-events-none" aria-hidden="true"></div>
        </label>
        <label class="relative bg-white border rounded-md px-3 py-2 flex items-center cursor-pointer focus:outline-none">
          <input type="radio" name="small-cards" value="option2" class="sr-only" aria-labelledby="small-option2-label">
          <span id="small-option2-label" class="block text-sm font-medium text-gray-900">M</span>
          <div class="absolute -inset-px rounded-md border-2 pointer-events-none" aria-hidden="true"></div>
        </label>
        <label class="relative bg-white border rounded-md px-3 py-2 flex items-center cursor-pointer focus:outline-none">
          <input type="radio" name="small-cards" value="option3" class="sr-only" aria-labelledby="small-option3-label">
          <span id="small-option3-label" class="block text-sm font-medium text-gray-900">L</span>
          <div class="absolute -inset-px rounded-md border-2 pointer-events-none" aria-hidden="true"></div>
        </label>
        <label class="relative bg-white border rounded-md px-3 py-2 flex items-center cursor-pointer focus:outline-none">
          <input type="radio" name="small-cards" value="option4" class="sr-only" aria-labelledby="small-option4-label">
          <span id="small-option4-label" class="block text-sm font-medium text-gray-900">XL</span>
          <div class="absolute -inset-px rounded-md border-2 pointer-events-none" aria-hidden="true"></div>
        </label>
      </div>
    `
  },
  {
    name: 'Stacked cards',
    html: `
      <div class="space-y-4">
        <label class="relative block bg-white border rounded-lg shadow-sm px-6 py-4 cursor-pointer sm:flex sm:justify-between focus:outline-none">
          <input type="radio" name="stacked-cards" value="option1" class="sr-only" aria-labelledby="stacked-option1-label" aria-describedby="stacked-option1-description-0 stacked-option1-description-1">
          <div class="flex items-center">
            <div class="text-sm">
              <p id="stacked-option1-label" class="font-medium text-gray-900">Basic Plan</p>
              <div id="stacked-option1-description-0" class="text-gray-500">
                <p class="sm:inline">For individuals</p>
              </div>
            </div>
          </div>
          <div id="stacked-option1-description-1" class="mt-2 flex text-sm sm:mt-0 sm:block sm:ml-4 sm:text-right">
            <div class="font-medium text-gray-900">$9.99/mo</div>
          </div>
          <div class="absolute -inset-px rounded-lg border-2 pointer-events-none" aria-hidden="true"></div>
        </label>
        <label class="relative block bg-white border rounded-lg shadow-sm px-6 py-4 cursor-pointer sm:flex sm:justify-between focus:outline-none">
          <input type="radio" name="stacked-cards" value="option2" class="sr-only" aria-labelledby="stacked-option2-label" aria-describedby="stacked-option2-description-0 stacked-option2-description-1">
          <div class="flex items-center">
            <div class="text-sm">
              <p id="stacked-option2-label" class="font-medium text-gray-900">Team Plan</p>
              <div id="stacked-option2-description-0" class="text-gray-500">
                <p class="sm:inline">For small teams</p>
              </div>
            </div>
          </div>
          <div id="stacked-option2-description-1" class="mt-2 flex text-sm sm:mt-0 sm:block sm:ml-4 sm:text-right">
            <div class="font-medium text-gray-900">$49.99/mo</div>
          </div>
          <div class="absolute -inset-px rounded-lg border-2 pointer-events-none" aria-hidden="true"></div>
        </label>
        <label class="relative block bg-white border rounded-lg shadow-sm px-6 py-4 cursor-pointer sm:flex sm:justify-between focus:outline-none">
          <input type="radio" name="stacked-cards" value="option3" class="sr-only" aria-labelledby="stacked-option3-label" aria-describedby="stacked-option3-description-0 stacked-option3-description-1">
          <div class="flex items-center">
            <div class="text-sm">
              <p id="stacked-option3-label" class="font-medium text-gray-900">Enterprise Plan</p>
              <div id="stacked-option3-description-0" class="text-gray-500">
                <p class="sm:inline">For large organizations</p>
              </div>
            </div>
          </div>
          <div id="stacked-option3-description-1" class="mt-2 flex text-sm sm:mt-0 sm:block sm:ml-4 sm:text-right">
            <div class="font-medium text-gray-900">$99.99/mo</div>
          </div>
          <div class="absolute -inset-px rounded-lg border-2 pointer-events-none" aria-hidden="true"></div>
        </label>
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