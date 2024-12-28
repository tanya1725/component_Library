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
                    <button @click="toggleCode(index)"
                        class="px-4 py-2 text-sm font-medium text-blue-600 bg-blue-100 rounded-md hover:bg-blue-200 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2">
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
import { Calendar, User, Clock, ArrowRight } from 'lucide-vue-next'

const showCode = ref({})

const variations = [
    {
        name: 'Three-column',
        html: `
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          ${Array.from({ length: 3 }, (_, index) => `
            <div class="bg-white rounded-lg shadow-md overflow-hidden">
              <div class="p-6">
                <h3 class="text-xl font-semibold mb-2">Blog Post Title ${index + 1}</h3>
                <p class="text-gray-600 mb-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                <div class="flex items-center text-sm text-gray-500">
                  <Calendar class="w-4 h-4 mr-2" />
                  <span>May 15, 2023</span>
                </div>
              </div>
            </div>
          `).join('')}
        </div>
      </div>
      `
    },
    {
        name: 'Three-column with images',
        html: `
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        ${Array.from({ length: 3 }, (_, index) => `
          <div class="bg-white rounded-lg shadow-md overflow-hidden">
            <img src="https://images.unsplash.com/photo-1496128858413-b36217c2ce36?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=3603&q=80" alt="Blog post image ${index + 1}" class="w-full h-48 object-cover" />
            <div class="p-6">
              <h3 class="text-xl font-semibold mb-2">Blog Post Title ${index + 1}</h3>
              <p class="text-gray-600 mb-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
              <div class="flex items-center text-sm text-gray-500">
                <User class="w-4 h-4 mr-2" />
                <span>John Doe</span>
              </div>
            </div>
          </div>
        `).join('')}
      </div>
    </div>
    `
    },
    {
        name: 'Three-column with background images',
        html: `
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        ${Array.from({ length: 3 }, (_, index) => `
          <div class="relative h-64 rounded-lg shadow-md overflow-hidden">
            <img src="https://images.unsplash.com/photo-1547586696-ea22b4d4235d?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=3270&q=80" alt="Blog post background ${index + 1}" class="absolute inset-0 w-full h-full object-cover" />
            <div class="absolute inset-0 bg-black bg-opacity-50"></div>
            <div class="absolute inset-0 p-6 flex flex-col justify-end">
              <h3 class="text-xl font-semibold mb-2 text-white">Blog Post Title ${index + 1}</h3>
              <div class="flex items-center text-sm text-gray-300">
                <Clock class="w-4 h-4 mr-2" />
                <span>5 min read</span>
              </div>
            </div>
          </div>
        `).join('')}
      </div>
    </div>
    `
    },
    {
        name: 'Single-column',
        html: `
      <div class="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
        ${Array.from({ length: 3 }, (_, index) => `
          <div class="bg-white rounded-lg shadow-md overflow-hidden mb-8">
            <div class="p-6">
              <h3 class="text-2xl font-semibold mb-2">Blog Post Title ${index + 1}</h3>
              <p class="text-gray-600 mb-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
              <div class="flex items-center justify-between text-sm text-gray-500">
                <div class="flex items-center">
                  <User class="w-4 h-4 mr-2" />
                  <span>John Doe</span>
                </div>
                <div class="flex items-center">
                  <Calendar class="w-4 h-4 mr-2" />
                  <span>May 15, 2023</span>
                </div>
              </div>
            </div>
          </div>
        `).join('')}
      </div>
      `
    },
    {
        name: 'Single-column with images',
        html: `
    <div class="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
      ${Array.from({ length: 3 }, (_, index) => `
        <div class="bg-white rounded-lg shadow-md overflow-hidden mb-8">
          <img src="https://images.unsplash.com/photo-1492724441997-5dc865305da7?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=3270&q=80" alt="Blog post image ${index + 1}" class="w-full h-64 object-cover" />
          <div class="p-6">
            <h3 class="text-2xl font-semibold mb-2">Blog Post Title ${index + 1}</h3>
            <p class="text-gray-600 mb-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
            <div class="flex items-center justify-between text-sm text-gray-500">
              <div class="flex items-center">
                <User class="w-4 h-4 mr-2" />
                <span>John Doe</span>
              </div>
              <div class="flex items-center">
                <Clock class="w-4 h-4 mr-2" />
                <span>5 min read</span>
              </div>
            </div>
          </div>
        </div>
      `).join('')}
    </div>
    `
    },
    {
        name: 'With featured post',
        html: `
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-10">
        <div class="mb-12">
        

              <h2 class="text-3xl font-bold mb-4">Featured Blog Post</h2>
              <p class="text-gray-600 mb-6">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
              <div class="flex items-center justify-between text-sm text-gray-500">
                <div class="flex items-center">
              </div>
            </div>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          ${Array.from({ length: 3 }, (_, index) => `
            <div class="bg-white rounded-lg shadow-md overflow-hidden">
              <div class="p-6">
                <h3 class="text-xl font-semibold mb-2">Blog Post Title ${index + 1}</h3>
                <p class="text-gray-600 mb-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                <div class="flex items-center text-sm text-gray-500">
                  <Clock class="w-4 h-4 mr-2" />
                  <span>5 min read</span>
                </div>
              </div>
            </div>
          `).join('')}
        </div>
      </div>
      `
    },
    {
        name: 'With photo and list',
        html: `
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div class="md:col-span-2 bg-white rounded-lg shadow-md overflow-hidden">
          <img src="https://images.unsplash.com/photo-1496128858413-b36217c2ce36?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=3603&q=80" alt="Main blog post image" class="w-full h-64 object-cover" />
          <div class="p-6">
            <h2 class="text-2xl font-bold mb-4">Main Blog Post</h2>
            <p class="text-gray-600 mb-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
            <div class="flex items-center justify-between text-sm text-gray-500">
              <div class="flex items-center">
                <User class="w-4 h-4 mr-2" />
                <span>John Doe</span>
              </div>
              <div class="flex items-center">
                <Calendar class="w-4 h-4 mr-2" />
                <span>May 15, 2023</span>
              </div>
            </div>
          </div>
        </div>
        <div class="bg-white rounded-lg shadow-md overflow-hidden">
          <div class="p-6">
            <h3 class="text-xl font-semibold mb-4">Recent Posts</h3>
            <ul class="space-y-4">
              ${Array.from({ length: 5 }, (_, index) => `
                <li class="flex items-center">
                  <img src="https://images.unsplash.com/photo-1547586696-ea22b4d4235d?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=3270&q=80" alt="Thumbnail ${index + 1}" class="w-16 h-16 object-cover rounded-md mr-4" />
                  <div>
                    <h4 class="font-semibold mb-1">Blog Post Title ${index + 1}</h4>
                    <div class="flex items-center text-sm text-gray-500">
                      <Clock class="w-4 h-4 mr-2" />
                      <span>5 min read</span>
                    </div>
                  </div>
                </li>
              `).join('')}
            </ul>
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