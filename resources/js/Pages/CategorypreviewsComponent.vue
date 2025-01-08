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
      name: 'Three column category grid',
      html: `
        <div class="bg-gray-50 py-12">
          <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold tracking-tight text-gray-900">Collections</h2>
            
            <div class="mt-8 grid grid-cols-1 gap-y-12 sm:grid-cols-2 sm:gap-x-6 lg:grid-cols-3 xl:gap-x-8">
              <div class="group relative">
                <div class="relative h-[300px] w-full overflow-hidden rounded-lg">
                  <img 
                    src="/placeholder.svg?height=300&width=400"
                    alt="Desk setup with computer and accessories"
                    class="h-full w-full object-cover object-center"
                  />
                </div>
                <div class="mt-4">
                  <p class="text-sm text-gray-500">Desk and Office</p>
                  <h3 class="mt-1 text-lg font-semibold text-gray-900">
                    <a href="#">
                      <span class="absolute inset-0"></span>
                      Work from home accessories
                    </h3>
                  </a>
                </div>
              </div>
  
              <div class="group relative">
                <div class="relative h-[300px] w-full overflow-hidden rounded-lg">
                  <img 
                    src="/placeholder.svg?height=300&width=400"
                    alt="Journal and pen on wooden desk"
                    class="h-full w-full object-cover object-center"
                  />
                </div>
                <div class="mt-4">
                  <p class="text-sm text-gray-500">Self-Improvement</p>
                  <h3 class="mt-1 text-lg font-semibold text-gray-900">
                    <a href="#">
                      <span class="absolute inset-0"></span>
                      Journals and note-taking
                    </h3>
                  </a>
                </div>
              </div>
  
              <div class="group relative">
                <div class="relative h-[300px] w-full overflow-hidden rounded-lg">
                  <img 
                    src="/placeholder.svg?height=300&width=400"
                    alt="Travel mugs and bottles"
                    class="h-full w-full object-cover object-center"
                  />
                </div>
                <div class="mt-4">
                  <p class="text-sm text-gray-500">Travel</p>
                  <h3 class="mt-1 text-lg font-semibold text-gray-900">
                    <a href="#">
                      <span class="absolute inset-0"></span>
                      Daily commute essentials
                    </h3>
                  </a>
                </div>
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
  .group:hover img {
    opacity: 0.75;
    transition: opacity 0.3s ease-in-out;
  }
  </style>