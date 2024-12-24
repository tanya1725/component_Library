<template>
    <div class="space-y-12">
      <div v-for="(variation, index) in variations" :key="index" class="bg-white rounded-lg shadow-md overflow-hidden">
        <div class="p-4 bg-gray-50 border-b">
          <h3 class="text-lg font-semibold text-gray-800">{{ variation.name }}</h3>
        </div>
        <div class="p-6">
          <div class="mb-4" v-html="variation.html"></div>
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
      name: 'About Page with Image Tiles',
      html: `
        <div class="bg-white">
          <div class="max-w-7xl mx-auto py-16 px-4 sm:py-24 sm:px-6 lg:px-8">
            <div class="text-center">
              <h2 class="text-base font-semibold text-indigo-600 tracking-wide uppercase">About Us</h2>
              <p class="mt-1 text-4xl font-extrabold text-gray-900 sm:text-5xl sm:tracking-tight lg:text-6xl">We love what we do</p>
              <p class="max-w-xl mt-5 mx-auto text-xl text-gray-500">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
            </div>
          </div>
          <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3">
              <div class="relative rounded-lg overflow-hidden">
                <img src="https://images.unsplash.com/photo-1551434678-e076c223a692?ixlib=rb-1.2.1&auto=format&fit=crop&w=2850&q=80" alt="Office space" class="w-full h-64 object-cover">
                <div class="absolute inset-0 bg-gray-900 bg-opacity-50 flex items-end p-4">
                  <h3 class="text-lg font-medium text-white">Our Workspace</h3>
                </div>
              </div>
              <div class="relative rounded-lg overflow-hidden">
                <img src="https://images.unsplash.com/photo-1521737711867-e3b97375f902?ixlib=rb-1.2.1&auto=format&fit=crop&w=2850&q=80" alt="Team meeting" class="w-full h-64 object-cover">
                <div class="absolute inset-0 bg-gray-900 bg-opacity-50 flex items-end p-4">
                  <h3 class="text-lg font-medium text-white">Our Team</h3>
                </div>
              </div>
              <div class="relative rounded-lg overflow-hidden">
                <img src="https://images.unsplash.com/photo-1531482615713-2afd69097998?ixlib=rb-1.2.1&auto=format&fit=crop&w=2850&q=80" alt="Product showcase" class="w-full h-64 object-cover">
                <div class="absolute inset-0 bg-gray-900 bg-opacity-50 flex items-end p-4">
                  <h3 class="text-lg font-medium text-white">Our Products</h3>
                </div>
              </div>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'Dark About Page',
      html: `
        <div class="bg-gray-900 text-white">
          <div class="max-w-7xl mx-auto py-16 px-4 sm:py-24 sm:px-6 lg:px-8">
            <div class="text-center">
              <h2 class="text-base font-semibold text-indigo-400 tracking-wide uppercase">About Us</h2>
              <p class="mt-1 text-4xl font-extrabold text-white sm:text-5xl sm:tracking-tight lg:text-6xl">Innovating for the Future</p>
              <p class="max-w-xl mt-5 mx-auto text-xl text-gray-400">We're on a mission to revolutionize the industry with cutting-edge technology and unparalleled expertise.</p>
            </div>
            
            <div class="mt-16 grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3">
              <div class="bg-gray-800 rounded-lg p-6">
                <div class="flex items-center justify-center w-12 h-12 rounded-md bg-indigo-500 text-white mb-4">
                  <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"></path>
                  </svg>
                </div>
                <h3 class="text-lg font-medium text-white mb-2">Innovation</h3>
                <p class="text-gray-400">Pushing boundaries and exploring new frontiers in technology.</p>
              </div>
              <div class="bg-gray-800 rounded-lg p-6">
                <div class="flex items-center justify-center w-12 h-12 rounded-md bg-indigo-500 text-white mb-4">
                  <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z"></path>
                  </svg>
                </div>
                <h3 class="text-lg font-medium text-white mb-2">Collaboration</h3>
                <p class="text-gray-400">Working together to achieve extraordinary results.</p>
              </div>
              <div class="bg-gray-800 rounded-lg p-6">
                <div class="flex items-center justify-center w-12 h-12 rounded-md bg-indigo-500 text-white mb-4">
                  <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path>
                  </svg>
                </div>
                <h3 class="text-lg font-medium text-white mb-2">Impact</h3>
                <p class="text-gray-400">Making a difference in the world through our work.</p>
              </div>
            </div>
            
            <div class="mt-16">
              <h3 class="text-lg font-medium text-white mb-6">Our Expertise</h3>
              <div class="space-y-4">
                <div class="bg-gray-800 rounded-lg p-4">
                  <div class="flex items-center justify-between mb-1">
                    <span class="text-sm font-medium text-indigo-400">Artificial Intelligence</span>
                    <span class="text-sm font-medium text-indigo-400">90%</span>
                  </div>
                  <div class="w-full bg-gray-700 rounded-full h-2.5">
                    <div class="bg-indigo-500 h-2.5 rounded-full" style="width: 90%"></div>
                  </div>
                </div>
                <div class="bg-gray-800 rounded-lg p-4">
                  <div class="flex items-center justify-between mb-1">
                    <span class="text-sm font-medium text-indigo-400">Machine Learning</span>
                    <span class="text-sm font-medium text-indigo-400">85%</span>
                  </div>
                  <div class="w-full bg-gray-700 rounded-full h-2.5">
                    <div class="bg-indigo-500 h-2.5 rounded-full" style="width: 85%"></div>
                  </div>
                </div>
                <div class="bg-gray-800 rounded-lg p-4">
                  <div class="flex items-center justify-between mb-1">
                    <span class="text-sm font-medium text-indigo-400">Data Analytics</span>
                    <span class="text-sm font-medium text-indigo-400">95%</span>
                  </div>
                  <div class="w-full bg-gray-700 rounded-full h-2.5">
                    <div class="bg-indigo-500 h-2.5 rounded-full" style="width: 95%"></div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      `
    }]
  
  const timeline = [
    {
      id: 1,
      content: 'Founded the company',
      date: 'Sep 2011',
      datetime: '2011-09-01',
    },
    {
      id: 2,
      content: 'Secured Series A funding',
      date: 'Mar 2014',
      datetime: '2014-03-15',
    },
    {
      id: 3,
      content: 'Launched our flagship product',
      date: 'Jun 2016',
      datetime: '2016-06-01',
    },
    {
      id: 4,
      content: 'Expanded to international markets',
      date: 'May 2018',
      datetime: '2018-05-10',
    },
    {
      id: 5,
      content: 'Reached 1 million users',
      date: 'Jan 2020',
      datetime: '2020-01-01',
    },
  ]
  
  const stats = [
    { name: 'Total Users', value: '1.5M+' },
    { name: 'Countries Served', value: '50+' },
    { name: 'Team Members', value: '250+' },
  ]
  
  const toggleCode = (index) => {
    showCode.value[index] = !showCode.value[index]
  }
  </script>
  
  <style scoped>
  /* Add any additional styles here if needed */
  </style>