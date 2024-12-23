<template>
    <div class="space-y-8">
      <div v-for="(variation, index) in variations" :key="index" class="bg-white rounded-lg shadow-md">
        <div class="p-4 bg-gray-50 border-b">
          <h3 class="text-lg font-semibold text-gray-800">{{ variation.name }}</h3>
        </div>
        <div class="p-4">
          <div class="mb-4">
            <div class="bg-gray-100 rounded-md" v-html="variation.html"></div>
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
  import { Menu, X, Home, Users, Folder, Calendar, Settings } from 'lucide-vue-next'
  
  const showCode = ref({})
  
  const variations = [
    {
      name: 'Brand sidebar with header',
      html: `
        <div class="flex h-screen bg-gray-100">
          <!-- Sidebar -->
          <aside class="w-64 bg-indigo-600">
            <div class="flex items-center justify-between h-16 px-4 bg-indigo-700">
              <span class="text-2xl font-semibold text-white">Logo</span>
              <button class="text-white focus:outline-none focus:ring-2 focus:ring-white">
                <Menu class="w-6 h-6" />
              </button>
            </div>
            <nav class="px-2 py-4">
              <a href="#" class="flex items-center px-4 py-2 text-white hover:bg-indigo-500 rounded-md">
                <Home class="w-5 h-5 mr-3" />
                Dashboard
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-white hover:bg-indigo-500 rounded-md">
                <Users class="w-5 h-5 mr-3" />
                Team
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-white hover:bg-indigo-500 rounded-md">
                <Folder class="w-5 h-5 mr-3" />
                Projects
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-white hover:bg-indigo-500 rounded-md">
                <Calendar class="w-5 h-5 mr-3" />
                Calendar
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-white hover:bg-indigo-500 rounded-md">
                <Settings class="w-5 h-5 mr-3" />
                Settings
              </a>
            </nav>
          </aside>
  
          <!-- Main Content -->
          <div class="flex-1">
            <header class="flex items-center justify-between h-16 px-6 bg-white border-b">
              <h1 class="text-2xl font-semibold">Dashboard</h1>
              <div class="flex items-center">
                <button class="mr-4 text-gray-600 hover:text-gray-800 focus:outline-none focus:ring-2 focus:ring-indigo-500">
                  <span class="sr-only">Notifications</span>
                  <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"></path>
                  </svg>
                </button>
                <button class="flex items-center text-gray-600 hover:text-gray-800 focus:outline-none focus:ring-2 focus:ring-indigo-500">
                  <img class="w-8 h-8 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="User avatar" />
                  <span class="ml-2">John Doe</span>
                </button>
              </div>
            </header>
            <main class="p-6">
              <p class="text-gray-700">Main content goes here.</p>
            </main>
          </div>
        </div>
      `
    },
    {
      name: 'Dark sidebar with header',
      html: `
        <div class="flex h-screen bg-gray-100">
          <!-- Sidebar -->
          <aside class="w-64 bg-gray-800">
            <div class="flex items-center justify-between h-16 px-4 bg-gray-900">
              <span class="text-2xl font-semibold text-white">Logo</span>
              <button class="text-gray-300 hover:text-white focus:outline-none focus:ring-2 focus:ring-white">
                <Menu class="w-6 h-6" />
              </button>
            </div>
            <nav class="px-2 py-4">
              <a href="#" class="flex items-center px-4 py-2 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md">
                <Home class="w-5 h-5 mr-3" />
                Dashboard
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md">
                <Users class="w-5 h-5 mr-3" />
                Team
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md">
                <Folder class="w-5 h-5 mr-3" />
                Projects
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md">
                <Calendar class="w-5 h-5 mr-3" />
                Calendar
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md">
                <Settings class="w-5 h-5 mr-3" />
                Settings
              </a>
            </nav>
          </aside>
  
          <!-- Main Content -->
          <div class="flex-1">
            <header class="flex items-center justify-between h-16 px-6 bg-white border-b">
              <h1 class="text-2xl font-semibold">Dashboard</h1>
              <div class="flex items-center">
                <button class="mr-4 text-gray-600 hover:text-gray-800 focus:outline-none focus:ring-2 focus:ring-gray-500">
                  <span class="sr-only">Notifications</span>
                  <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"></path>
                  </svg>
                </button>
                <button class="flex items-center text-gray-600 hover:text-gray-800 focus:outline-none focus:ring-2 focus:ring-gray-500">
                  <img class="w-8 h-8 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="User avatar" />
                  <span class="ml-2">John Doe</span>
                </button>
              </div>
            </header>
            <main class="p-6">
              <p class="text-gray-700">Main content goes here.</p>
            </main>
          </div>
        </div>
      `
    },
    {
      name: 'Light sidebar with header',
      html: `
        <div class="flex h-screen bg-gray-100">
          <!-- Sidebar -->
          <aside class="w-64 bg-white border-r">
            <div class="flex items-center justify-between h-16 px-4 border-b">
              <span class="text-2xl font-semibold text-gray-800">Logo</span>
              <button class="text-gray-600 hover:text-gray-800 focus:outline-none focus:ring-2 focus:ring-gray-500">
                <Menu class="w-6 h-6" />
              </button>
            </div>
            <nav class="px-2 py-4">
              <a href="#" class="flex items-center px-4 py-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Home class="w-5 h-5 mr-3 text-gray-500" />
                Dashboard
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Users class="w-5 h-5 mr-3 text-gray-500" />
                Team
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Folder class="w-5 h-5 mr-3 text-gray-500" />
                Projects
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Calendar class="w-5 h-5 mr-3 text-gray-500" />
                Calendar
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Settings class="w-5 h-5 mr-3 text-gray-500" />
                Settings
              </a>
            </nav>
          </aside>
  
          <!-- Main Content -->
          <div class="flex-1">
            <header class="flex items-center justify-between h-16 px-6 bg-white border-b">
              <h1 class="text-2xl font-semibold text-gray-800">Dashboard</h1>
              <div class="flex items-center">
                <button class="mr-4 text-gray-600 hover:text-gray-800 focus:outline-none focus:ring-2 focus:ring-gray-500">
                  <span class="sr-only">Notifications</span>
                  <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"></path>
                  </svg>
                </button>
                <button class="flex items-center text-gray-600 hover:text-gray-800 focus:outline-none focus:ring-2 focus:ring-gray-500">
                  <img class="w-8 h-8 rounded-full" src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="User avatar" />
                  <span class="ml-2">John Doe</span>
                </button>
              </div>
            </header>
            <main class="p-6">
              <p class="text-gray-700">Main content goes here.</p>
            </main>
          </div>
        </div>
      `
    },
    {
      name: 'Brand sidebar',
      html:`
        <div class="flex h-screen bg-gray-100">
          <!-- Sidebar -->
          <aside class="w-64 bg-indigo-600">
            <div class="flex items-center justify-between h-16 px-4 bg-indigo-700">
              <span class="text-2xl font-semibold text-white">Logo</span>
              <button class="text-white focus:outline-none focus:ring-2 focus:ring-white">
                <Menu class="w-6 h-6" />
              </button>
            </div>
            <nav class="px-2 py-4">
              <a href="#" class="flex items-center px-4 py-2 text-white hover:bg-indigo-500 rounded-md">
                <Home class="w-5 h-5 mr-3" />
                Dashboard
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-white hover:bg-indigo-500 rounded-md">
                <Users class="w-5 h-5 mr-3" />
                Team
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-white hover:bg-indigo-500 rounded-md">
                <Folder class="w-5 h-5 mr-3" />
                Projects
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-white hover:bg-indigo-500 rounded-md">
                <Calendar class="w-5 h-5 mr-3" />
                Calendar
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-white hover:bg-indigo-500 rounded-md">
                <Settings class="w-5 h-5 mr-3" />
                Settings
              </a>
            </nav>
          </aside>
  
          <!-- Main Content -->
          <div class="flex-1 p-6">
            <h1 class="text-2xl font-semibold text-gray-800 mb-4">Dashboard</h1>
            <p class="text-gray-700">Main content goes here.</p>
          </div>
        </div>
      `
    },
    {
      name: 'Dark sidebar',
      html: `
        <div class="flex h-screen bg-gray-100">
          <!-- Sidebar -->
          <aside class="w-64 bg-gray-800">
            <div class="flex items-center justify-between h-16 px-4 bg-gray-900">
              <span class="text-2xl font-semibold text-white">Logo</span>
              <button class="text-gray-300 hover:text-white focus:outline-none focus:ring-2 focus:ring-white">
                <Menu class="w-6 h-6" />
              </button>
            </div>
            <nav class="px-2 py-4">
              <a href="#" class="flex items-center px-4 py-2 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md">
                <Home class="w-5 h-5 mr-3" />
                Dashboard
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md">
                <Users class="w-5 h-5 mr-3" />
                Team
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md">
                <Folder class="w-5 h-5 mr-3" />
                Projects
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md">
                <Calendar class="w-5 h-5 mr-3" />
                Calendar
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-300 hover:bg-gray-700 hover:text-white rounded-md">
                <Settings class="w-5 h-5 mr-3" />
                Settings
              </a>
            </nav>
          </aside>
  
          <!-- Main Content -->
          <div class="flex-1 p-6">
            <h1 class="text-2xl font-semibold text-gray-800 mb-4">Dashboard</h1>
            <p class="text-gray-700">Main content goes here.</p>
          </div>
        </div>
      `
    },
    {
      name: 'Light sidebar with constrained content area',
      html: `
        <div class="flex h-screen bg-gray-100">
          <!-- Sidebar -->
          <aside class="w-64 bg-white border-r">
            <div class="flex items-center justify-between h-16 px-4 border-b">
              <span class="text-2xl font-semibold text-gray-800">Logo</span>
              <button class="text-gray-600 hover:text-gray-800 focus:outline-none focus:ring-2 focus:ring-gray-500">
                <Menu class="w-6 h-6" />
              </button>
            </div>
            <nav class="px-2 py-4">
              <a href="#" class="flex items-center px-4 py-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Home class="w-5 h-5 mr-3 text-gray-500" />
                Dashboard
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Users class="w-5 h-5 mr-3 text-gray-500" />
                Team
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Folder class="w-5 h-5 mr-3 text-gray-500" />
                Projects
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Calendar class="w-5 h-5 mr-3 text-gray-500" />
                Calendar
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Settings class="w-5 h-5 mr-3 text-gray-500" />
                Settings
              </a>
            </nav>
          </aside>
  
          <!-- Main Content -->
          <div class="flex-1 overflow-hidden">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6">
              <h1 class="text-2xl font-semibold text-gray-800 mb-4">Dashboard</h1>
              <div class="bg-white shadow rounded-lg p-6">
                <p class="text-gray-700">Main content goes here, constrained to a maximum width.</p>
              </div>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'Light sidebar with off-white background',
      html: `
        <div class="flex h-screen bg-gray-50">
          <!-- Sidebar -->
          <aside class="w-64 bg-white border-r">
            <div class="flex items-center justify-between h-16 px-4 border-b">
              <span class="text-2xl font-semibold text-gray-800">Logo</span>
              <button class="text-gray-600 hover:text-gray-800 focus:outline-none focus:ring-2 focus:ring-gray-500">
                <Menu class="w-6 h-6" />
              </button>
            </div>
            <nav class="px-2 py-4">
              <a href="#" class="flex items-center px-4 py-2 text-gray-700 bg-gray-100 rounded-md">
                <Home class="w-5 h-5 mr-3 text-gray-500" />
                Dashboard
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Users class="w-5 h-5 mr-3 text-gray-500" />
                Team
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Folder class="w-5 h-5 mr-3 text-gray-500" />
                Projects
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Calendar class="w-5 h-5 mr-3 text-gray-500" />
                Calendar
              </a>
              <a href="#" class="flex items-center px-4 py-2 mt-2 text-gray-700 hover:bg-gray-100 rounded-md">
                <Settings class="w-5 h-5 mr-3 text-gray-500" />
                Settings
              </a>
            </nav>
          </aside>
  
          <!-- Main Content -->
          <div class="flex-1 p-6">
            <h1 class="text-2xl font-semibold text-gray-800 mb-4">Dashboard</h1>
            <div class="bg-white shadow rounded-lg p-6">
              <p class="text-gray-700">Main content goes here, on an off-white background.</p>
            </div>
          </div>
        </div>
      `
    },
  ]
  
  const toggleCode = (index) => {
    showCode.value[index] = !showCode.value[index]
  }
  </script>
  
  <style scoped>
  /* Add any additional styles here if needed */
  </style>