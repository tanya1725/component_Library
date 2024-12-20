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
      name: 'Input with inline leading add-on and trailing dropdown',
      html: `
        <div class="flex">
          <span class="inline-flex items-center px-3 rounded-l-md border border-r-0 border-gray-300 bg-gray-50 text-gray-500 text-sm">
            http://
          </span>
          <input type="text" class="flex-1 block w-full rounded-none sm:text-sm border-gray-300" placeholder="www.example.com">
          <select class="inline-flex items-center px-3 rounded-r-md border border-l-0 border-gray-300 bg-gray-50 text-gray-500 text-sm">
            <option>.com</option>
            <option>.org</option>
            <option>.net</option>
          </select>
        </div>
      `
    },
    {
      name: 'Input with label',
      html: `
        <div>
          <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
          <input type="email" id="email" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50" placeholder="you@example.com">
        </div>
      `
    },
    {
      name: 'Input with label and help text',
      html: `
        <div>
          <label for="username" class="block text-sm font-medium text-gray-700">Username</label>
          <input type="text" id="username" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50" placeholder="johndoe">
          <p class="mt-2 text-sm text-gray-500">This will be your public display name.</p>
        </div>
      `
    },
    {
      name: 'Input with validation error',
      html: `
        <div>
          <label for="email-error" class="block text-sm font-medium text-red-700">Email</label>
          <input type="email" id="email-error" class="mt-1 block w-full rounded-md border-red-300 text-red-900 placeholder-red-300 focus:border-red-500 focus:ring-red-500" placeholder="you@example.com" value="invalid-email">
          <p class="mt-2 text-sm text-red-600">Please enter a valid email address.</p>
        </div>
      `
    },
    {
      name: 'Input with disabled state',
      html: `
        <div>
          <label for="disabled-input" class="block text-sm font-medium text-gray-500">Disabled input</label>
          <input type="text" id="disabled-input" class="mt-1 bg-gray-100 block w-full rounded-md border-gray-300 text-gray-500 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50" disabled value="Disabled input">
        </div>
      `
    },
    {
      name: 'Input with hidden label',
      html: `
        <div>
          <label for="hidden-label" class="sr-only">Email</label>
          <input type="email" id="hidden-label" class="block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50" placeholder="Enter your email">
        </div>
      `
    },
    {
      name: 'Input with corner hint',
      html: `
        <div>
          <div class="flex justify-between">
            <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
            <span class="text-sm text-gray-500">Max. 12 characters</span>
          </div>
          <input type="password" id="password" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50">
        </div>
      `
    },
    {
      name: 'Input with leading icon',
      html: `
        <div class="relative rounded-md shadow-sm">
          <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
            <svg class="h-5 w-5 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
              <path d="M2.003 5.884L10 9.882l7.997-3.998A2 2 0 0016 4H4a2 2 0 00-1.997 1.884z" />
              <path d="M18 8.118l-8 4-8-4V14a2 2 0 002 2h12a2 2 0 002-2V8.118z" />
            </svg>
          </div>
          <input type="email" class="block w-full pl-10 sm:text-sm border-gray-300 rounded-md" placeholder="you@example.com">
        </div>
      `
    },
    {
      name: 'Input with trailing icon',
      html: `
        <div class="relative rounded-md shadow-sm">
          <input type="text" class="block w-full pr-10 sm:text-sm border-gray-300 rounded-md" placeholder="Search">
          <div class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none">
            <svg class="h-5 w-5 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
              <path fill-rule="evenodd" d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z" clip-rule="evenodd" />
            </svg>
          </div>
        </div>
      `
    },
    {
      name: 'Input with add-on',
      html: `
        <div class="flex rounded-md shadow-sm">
          <span class="inline-flex items-center px-3 rounded-l-md border border-r-0 border-gray-300 bg-gray-50 text-gray-500 text-sm">
            https://
          </span>
          <input type="text" class="flex-1 block w-full rounded-none rounded-r-md sm:text-sm border-gray-300" placeholder="www.example.com">
        </div>
      `
    },
    {
      name: 'Input with inline add-on',
      html: `
        <div class="flex rounded-md shadow-sm">
          <input type="text" class="flex-1 block w-full rounded-none rounded-l-md sm:text-sm border-gray-300" placeholder="miguel">
          <span class="inline-flex items-center px-3 rounded-r-md border border-l-0 border-gray-300 bg-gray-50 text-gray-500 text-sm">
            @example.com
          </span>
        </div>
      `
    },
    {
      name: 'Input with inline leading and trailing add-ons',
      html: `
        <div class="flex rounded-md shadow-sm">
          <span class="inline-flex items-center px-3 rounded-l-md border border-r-0 border-gray-300 bg-gray-50 text-gray-500 text-sm">
            $
          </span>
          <input type="text" class="flex-1 block w-full rounded-none sm:text-sm border-gray-300" placeholder="0.00">
          <span class="inline-flex items-center px-3 rounded-r-md border border-l-0 border-gray-300 bg-gray-50 text-gray-500 text-sm">
            USD
          </span>
        </div>
      `
    },
    {
      name: 'Input with inline leading dropdown',
      html: `
        <div class="flex rounded-md shadow-sm">
          <select class="inline-flex items-center px-3 rounded-l-md border border-r-0 border-gray-300 bg-gray-50 text-gray-500 text-sm">
            <option>https://</option>
            <option>http://</option>
          </select>
          <input type="text" class="flex-1 block w-full rounded-none rounded-r-md sm:text-sm border-gray-300" placeholder="www.example.com">
        </div>
      `
    },
    {
      name: 'Input with leading icon and trailing button',
      html: `
        <div class="relative rounded-md shadow-sm">
          <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
            <svg class="h-5 w-5 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
              <path fill-rule="evenodd" d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z" clip-rule="evenodd" />
            </svg>
          </div>
          <input type="text" class="block w-full pl-10 pr-12 sm:text-sm border-gray-300 rounded-md" placeholder="Search">
          <div class="absolute inset-y-0 right-0 flex items-center">
            <button type="button" class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-r-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
              Search
            </button>
          </div>
        </div>
      `
    },
    {
      name: 'Inputs with shared borders',
      html: `
        <div class="isolate -space-y-px rounded-md shadow-sm">
          <div class="relative border border-gray-300 rounded-md rounded-b-none px-3 py-2 focus-within:z-10 focus-within:ring-1 focus-within:ring-indigo-600 focus-within:border-indigo-600">
            <label for="name" class="block text-xs font-medium text-gray-700">Name</label>
            <input type="text" id="name" class="block w-full border-0 p-0 text-gray-900 placeholder-gray-500 focus:ring-0 sm:text-sm" placeholder="Jane Smith">
          </div>
          <div class="relative border border-gray-300 rounded-md rounded-t-none px-3 py-2 focus-within:z-10 focus-within:ring-1 focus-within:ring-indigo-600 focus-within:border-indigo-600">
            <label for="job-title" class="block text-xs font-medium text-gray-700">Job Title</label>
            <input type="text" id="job-title" class="block w-full border-0 p-0 text-gray-900 placeholder-gray-500 focus:ring-0 sm:text-sm" placeholder="Software Engineer">
          </div>
        </div>
      `
    },
    {
      name: 'Input with inset label',
      html: `
        <div class="relative border border-gray-300 rounded-md px-3 py-2 shadow-sm focus-within:ring-1 focus-within:ring-indigo-600 focus-within:border-indigo-600">
          <label for="name" class="absolute -top-2 left-2 -mt-px inline-block px-1 bg-white text-xs font-medium text-gray-900">Name</label>
          <input type="text" id="name" class="block w-full border-0 p-0 text-gray-900 placeholder-gray-500 focus:ring-0 sm:text-sm" placeholder="Jane Smith">
        </div>
      `
    },
    {
      name: 'Inputs with inset labels and shared borders',
      html: `
        <div class="isolate -space-y-px rounded-md shadow-sm">
          <div class="relative border border-gray-300 rounded-md rounded-b-none px-3 py-2 focus-within:z-10 focus-within:ring-1 focus-within:ring-indigo-600 focus-within:border-indigo-600">
            <label for="first-name" class="absolute -top-2 left-2 -mt-px inline-block px-1 bg-white text-xs font-medium text-gray-900">First name</label>
            <input type="text" id="first-name" class="block w-full border-0 p-0 text-gray-900 placeholder-gray-500 focus:ring-0 sm:text-sm" placeholder="Jane">
          </div>
          <div class="relative border border-gray-300 rounded-md rounded-t-none px-3 py-2 focus-within:z-10 focus-within:ring-1 focus-within:ring-indigo-600 focus-within:border-indigo-600">
            <label for="last-name" class="absolute -top-2 left-2 -mt-px inline-block px-1 bg-white text-xs font-medium text-gray-900">Last name</label>
            <input type="text" id="last-name" class="block w-full border-0 p-0 text-gray-900 placeholder-gray-500 focus:ring-0 sm:text-sm" placeholder="Smith">
          </div>
        </div>
      `
    },
    {
      name: 'Input with overlapping label',
      html: `
        <div class="relative">
          <input type="text" id="floating-input" class="block px-2.5 pb-2.5 pt-4 w-full text-sm text-gray-900 bg-transparent rounded-lg border-1 border-gray-300 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 peer" placeholder=" " />
          <label for="floating-input" class="absolute text-sm text-gray-500 duration-300 transform -translate-y-4 scale-75 top-2 z-10 origin-[0] bg-white px-2 peer-focus:px-2 peer-focus:text-blue-600 peer-placeholder-shown:scale-100 peer-placeholder-shown:-translate-y-1/2 peer-placeholder-shown:top-1/2 peer-focus:top-2 peer-focus:scale-75 peer-focus:-translate-y-4 left-1">Floating label</label>
        </div>
      `
    },
    {
      name: 'Input with pill shape',
      html: `
        <input type="text" class="mt-1 block w-full px-3 py-2 bg-white border border-gray-300 rounded-full shadow-sm placeholder-gray-400 focus:outline-none focus:border-sky-500 focus:ring-1 focus:ring-sky-500" placeholder="Enter text here">
      `
    },
    {
      name: 'Input with gray background and bottom border',
      html: `
        <input type="text" class="mt-1 block w-full px-3 py-2 bg-gray-100 border-0 border-b-2 border-gray-200 focus:ring-0 focus:border-black" placeholder="Enter text here">
      `
    },
    {
      name: 'Input with keyboard shortcut',
      html: `
        <div class="flex rounded-md shadow-sm">
          <input type="text" class="flex-1 block w-full rounded-none rounded-l-md sm:text-sm border-gray-300" placeholder="Enter command">
          <span class="inline-flex items-center px-3 rounded-r-md border border-l-0 border-gray-300 bg-gray-50 text-gray-500 text-sm">
            ⌘K
          </span>
        </div>
      `
    },
    { name: 'Text', html: '<input type="text" placeholder="Text Input" class="border rounded p-2">' },
    { name: 'Password', html: '<input type="password" placeholder="Password Input" class="border rounded p-2">' },
    { name: 'Number', html: '<input type="number" placeholder="Number Input" class="border rounded p-2">' },
  ]
  
  
  const toggleCode = (index) => {
    showCode.value[index] = !showCode.value[index]
  }
  </script>