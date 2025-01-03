<template>
    <div class="space-y-8 p-8">
      <div v-for="(variation, index) in variations" :key="index" class="bg-white rounded-lg shadow-md w-full">
        <div class="p-4 bg-gray-50 border-b">
          <h3 class="text-lg font-semibold text-gray-800">{{ variation.name }}</h3>
        </div>
        <div class="p-4">
          <div class="mb-4">
            <div class="p-4 bg-gray-50 rounded-md">
              <!-- Main content -->
              <div class="min-h-screen bg-white">
                <div class="mx-auto max-w-7xl">
                  <div class="flex items-center justify-between pb-6">
                    <h1 class="text-4xl font-bold text-gray-900">New Arrivals</h1>
                    <div class="flex items-center gap-4">
                      <div class="relative">
                        <button 
                          @click="toggleSort"
                          class="flex items-center gap-2 text-sm text-gray-500 hover:text-gray-900"
                        >
                          Sort
                          <svg 
                            class="h-5 w-5" 
                            :class="{ 'rotate-180': showSort }"
                            fill="none" 
                            viewBox="0 0 24 24" 
                            stroke="currentColor"
                          >
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                          </svg>
                        </button>
                        <div v-if="showSort" class="absolute right-0 mt-2 w-48 rounded-md bg-white shadow-lg ring-1 ring-black ring-opacity-5">
                          <div class="py-1">
                            <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Most Popular</a>
                            <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Best Rating</a>
                            <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Newest</a>
                            <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Price: Low to High</a>
                            <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Price: High to Low</a>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
  
                  <div class="grid grid-cols-1 gap-x-8 lg:grid-cols-4">
                    <div class="hidden lg:block">
                      <ul class="space-y-4 border-b border-gray-200 pb-6 text-sm">
                        <li><a href="#" class="text-gray-900 hover:text-gray-600">Totes</a></li>
                        <li><a href="#" class="text-gray-900 hover:text-gray-600">Backpacks</a></li>
                        <li><a href="#" class="text-gray-900 hover:text-gray-600">Travel Bags</a></li>
                        <li><a href="#" class="text-gray-900 hover:text-gray-600">Hip Bags</a></li>
                        <li><a href="#" class="text-gray-900 hover:text-gray-600">Laptop Sleeves</a></li>
                      </ul>
  
                      <div v-for="(section, sectionName) in sections" :key="sectionName" class="border-b border-gray-200 py-6">
                        <div class="flex items-center justify-between">
                          <h3 class="text-sm font-medium text-gray-900">{{ sectionName }}</h3>
                          <button @click="toggleSection(sectionName.toLowerCase())" class="text-gray-400 hover:text-gray-500">
                            <svg 
                              class="h-5 w-5" 
                              :class="{ 'rotate-180': openSections[sectionName.toLowerCase()] }"
                              fill="none" 
                              viewBox="0 0 24 24" 
                              stroke="currentColor"
                            >
                              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                            </svg>
                          </button>
                        </div>
                        <div v-show="openSections[sectionName.toLowerCase()]" class="mt-4 space-y-4">
                          <div v-for="item in section" :key="item.value" class="flex items-center">
                            <input
                              :id="sectionName.toLowerCase() + '-' + item.value"
                              type="checkbox"
                              :checked="(sectionName === 'Color' && item.value === 'blue') || (sectionName === 'Category' && item.value === 'travel')"
                              class="h-4 w-4 rounded border-gray-300 text-blue-600 focus:ring-blue-500"
                            />
                            <label :for="sectionName.toLowerCase() + '-' + item.value" class="ml-3 text-sm text-gray-600">
                              {{ item.label }}
                            </label>
                          </div>
                        </div>
                      </div>
                    </div>
  
                    <div class="lg:col-span-3">
                      <div class="h-96 rounded border-2 border-dashed border-gray-200"></div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
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
  const showSort = ref(false)
  const openSections = ref({
    color: true,
    category: true,
    size: true
  })
  
  const sections = {
    'Color': [
      { label: 'White', value: 'white' },
      { label: 'Beige', value: 'beige' },
      { label: 'Blue', value: 'blue' },
      { label: 'Brown', value: 'brown' },
      { label: 'Green', value: 'green' },
      { label: 'Purple', value: 'purple' }
    ],
    'Category': [
      { label: 'New Arrivals', value: 'new-arrivals' },
      { label: 'Sale', value: 'sale' },
      { label: 'Travel', value: 'travel' },
      { label: 'Organization', value: 'organization' },
      { label: 'Accessories', value: 'accessories' }
    ],
    'Size': [
      { label: '2L', value: '2l' },
      { label: '6L', value: '6l' },
      { label: '12L', value: '12l' },
      { label: '18L', value: '18l' },
      { label: '20L', value: '20l' },
      { label: '40L', value: '40l' }
    ]
  }
  
  const variations = [
    {
      name: 'With inline actions and expandable sidebar filters',
      html: `  <div class="min-h-screen bg-white p-8">
    <div class="mx-auto max-w-7xl">
      <div class="flex items-center justify-between pb-6">
        <h1 class="text-4xl font-bold text-gray-900">New Arrivals</h1>
        <div class="flex items-center gap-4">
          <div class="relative">
            <button 
              @click="toggleSort"
              class="flex items-center gap-2 text-sm text-gray-500 hover:text-gray-900"
            >
              Sort
              <svg 
                class="h-5 w-5" 
                :class="{ 'rotate-180': showSort }"
                fill="none" 
                viewBox="0 0 24 24" 
                stroke="currentColor"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
              </svg>
            </button>
            <!-- Sort dropdown -->
            <div v-if="showSort" class="absolute right-0 mt-2 w-48 rounded-md bg-white shadow-lg ring-1 ring-black ring-opacity-5">
              <div class="py-1">
                <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Most Popular</a>
                <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Best Rating</a>
                <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Newest</a>
                <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Price: Low to High</a>
                <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Price: High to Low</a>
              </div>
            </div>
          </div>
          <button class="text-gray-500 hover:text-gray-900">
            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
          </button>
        </div>
      </div>

      <div class="grid grid-cols-1 gap-x-8 lg:grid-cols-4">
        <!-- Filters sidebar -->
        <div class="hidden lg:block">
          <!-- Categories -->
          <ul class="space-y-4 border-b border-gray-200 pb-6 text-sm">
            <li><a href="#" class="text-gray-900 hover:text-gray-600">Totes</a></li>
            <li><a href="#" class="text-gray-900 hover:text-gray-600">Backpacks</a></li>
            <li><a href="#" class="text-gray-900 hover:text-gray-600">Travel Bags</a></li>
            <li><a href="#" class="text-gray-900 hover:text-gray-600">Hip Bags</a></li>
            <li><a href="#" class="text-gray-900 hover:text-gray-600">Laptop Sleeves</a></li>
          </ul>

          <!-- Color filter -->
          <div class="border-b border-gray-200 py-6">
            <div class="flex items-center justify-between">
              <h3 class="text-sm font-medium text-gray-900">Color</h3>
              <button @click="toggleSection('color')" class="text-gray-400 hover:text-gray-500">
                <svg 
                  class="h-5 w-5" 
                  :class="{ 'rotate-180': openSections.color }"
                  fill="none" 
                  viewBox="0 0 24 24" 
                  stroke="currentColor"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                </svg>
              </button>
            </div>
            <div v-show="openSections.color" class="mt-4 space-y-4">
              <div v-for="color in colors" :key="color.value" class="flex items-center">
                <input
                  :id="'color-' + color.value"
                  type="checkbox"
                  :checked="color.value === 'blue'"
                  class="h-4 w-4 rounded border-gray-300 text-blue-600 focus:ring-blue-500"
                />
                <label :for="'color-' + color.value" class="ml-3 text-sm text-gray-600">
                  {{ color.label }}
                </label>
              </div>
            </div>
          </div>

          <!-- Category filter -->
          <div class="border-b border-gray-200 py-6">
            <div class="flex items-center justify-between">
              <h3 class="text-sm font-medium text-gray-900">Category</h3>
              <button @click="toggleSection('category')" class="text-gray-400 hover:text-gray-500">
                <svg 
                  class="h-5 w-5" 
                  :class="{ 'rotate-180': openSections.category }"
                  fill="none" 
                  viewBox="0 0 24 24" 
                  stroke="currentColor"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                </svg>
              </button>
            </div>
            <div v-show="openSections.category" class="mt-4 space-y-4">
              <div v-for="category in categories" :key="category.value" class="flex items-center">
                <input
                  :id="'category-' + category.value"
                  type="checkbox"
                  :checked="category.value === 'travel'"
                  class="h-4 w-4 rounded border-gray-300 text-blue-600 focus:ring-blue-500"
                />
                <label :for="'category-' + category.value" class="ml-3 text-sm text-gray-600">
                  {{ category.label }}
                </label>
              </div>
            </div>
          </div>

          <!-- Size filter -->
          <div class="border-b border-gray-200 py-6">
            <div class="flex items-center justify-between">
              <h3 class="text-sm font-medium text-gray-900">Size</h3>
              <button @click="toggleSection('size')" class="text-gray-400 hover:text-gray-500">
                <svg 
                  class="h-5 w-5" 
                  :class="{ 'rotate-180': openSections.size }"
                  fill="none" 
                  viewBox="0 0 24 24" 
                  stroke="currentColor"
                >
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                </svg>
              </button>
            </div>
            <div v-show="openSections.size" class="mt-4 space-y-4">
              <div v-for="size in sizes" :key="size.value" class="flex items-center">
                <input
                  :id="'size-' + size.value"
                  type="checkbox"
                  class="h-4 w-4 rounded border-gray-300 text-blue-600 focus:ring-blue-500"
                />
                <label :for="'size-' + size.value" class="ml-3 text-sm text-gray-600">
                  {{ size.label }}
                </label>
              </div>
            </div>
          </div>
        </div>

        <!-- Product grid -->
        <div class="lg:col-span-3">
          <!-- Add your product grid here -->
          <div class="h-96 rounded border-2 border-dashed border-gray-200"></div>
        </div>
      </div>
    </div>
  </div>`
    }
  ]
  
  const toggleSort = () => {
    showSort.value = !showSort.value
  }
  
  const toggleSection = (section) => {
    openSections.value[section] = !openSections.value[section]
  }
  
  const toggleCode = (index) => {
    showCode.value[index] = !showCode.value[index]
  }
  </script>