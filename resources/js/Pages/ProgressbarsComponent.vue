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
  import { Check } from 'lucide-vue-next'
  
  const showCode = ref({})
  
  const variations = [
    {
      name: 'Simple',
      html: `
        <div class="w-full max-w-3xl mx-auto">
          <div class="flex justify-between mb-8">
            <div class="w-1/3">
              <div class="h-1 bg-indigo-600"></div>
              <div class="mt-2">
                <div class="text-xs text-indigo-600 font-medium">Step 1</div>
                <div class="text-sm font-medium">Job details</div>
              </div>
            </div>
            <div class="w-1/3">
              <div class="h-1 bg-indigo-600"></div>
              <div class="mt-2">
                <div class="text-xs text-indigo-600 font-medium">Step 2</div>
                <div class="text-sm font-medium">Application form</div>
              </div>
            </div>
            <div class="w-1/3">
              <div class="h-1 bg-gray-200"></div>
              <div class="mt-2">
                <div class="text-xs text-gray-500 font-medium">Step 3</div>
                <div class="text-sm font-medium">Preview</div>
              </div>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'Panels',
      html: `
        <div class="w-full max-w-3xl mx-auto">
          <div class="relative flex items-center justify-between">
            <div class="flex items-center">
              <div class="w-10 h-10 flex items-center justify-center rounded-full bg-indigo-600 text-white">
                <svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <path d="M20 6L9 17L4 12" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </div>
              <div class="ml-3">
                <div class="text-sm font-medium">Job details</div>
              </div>
            </div>
            <div class="flex-1 mx-4">
              <div class="h-0.5 bg-indigo-600"></div>
            </div>
            <div class="flex items-center">
              <div class="w-10 h-10 flex items-center justify-center rounded-full border-2 border-indigo-600 text-indigo-600">
                <span class="text-sm font-medium">02</span>
              </div>
              <div class="ml-3">
                <div class="text-sm font-medium text-indigo-600">Application form</div>
              </div>
            </div>
            <div class="flex-1 mx-4">
              <div class="h-0.5 bg-gray-200"></div>
            </div>
            <div class="flex items-center">
              <div class="w-10 h-10 flex items-center justify-center rounded-full border-2 border-gray-200 text-gray-400">
                <span class="text-sm font-medium">03</span>
              </div>
              <div class="ml-3">
                <div class="text-sm font-medium text-gray-500">Preview</div>
              </div>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'Bullets',
      html: `
        <div class="w-full max-w-3xl mx-auto">
          <div class="flex items-center justify-center gap-2">
            <div class="w-2 h-2 rounded-full bg-indigo-600"></div>
            <div class="w-2 h-2 rounded-full bg-indigo-600"></div>
            <div class="w-2 h-2 rounded-full bg-gray-200"></div>
            <div class="w-2 h-2 rounded-full bg-gray-200"></div>
            <div class="text-sm text-gray-600 ml-2">Step 2 of 4</div>
          </div>
        </div>
      `
    },
    {
      name: 'Panels with border',
      html: `
        <div class="w-full max-w-3xl mx-auto p-4 border rounded-lg">
          <div class="relative flex items-center justify-between">
            <div class="flex items-center">
              <div class="w-10 h-10 flex items-center justify-center rounded-full bg-indigo-600 text-white">
                <svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                  <path d="M20 6L9 17L4 12" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </div>
              <div class="ml-3">
                <div class="text-sm font-medium">Job Details</div>
                <div class="text-xs text-gray-500">Vitae sed mi luctus laoreet.</div>
              </div>
            </div>
            <div class="flex-1 mx-4">
              <div class="h-0.5 bg-indigo-600"></div>
            </div>
            <div class="flex items-center">
              <div class="w-10 h-10 flex items-center justify-center rounded-full border-2 border-indigo-600 text-indigo-600">
                <span class="text-sm font-medium">02</span>
              </div>
              <div class="ml-3">
                <div class="text-sm font-medium text-indigo-600">Application form</div>
                <div class="text-xs text-gray-500">Cursus semper viverra.</div>
              </div>
            </div>
            <div class="flex-1 mx-4">
              <div class="h-0.5 bg-gray-200"></div>
            </div>
            <div class="flex items-center">
              <div class="w-10 h-10 flex items-center justify-center rounded-full border-2 border-gray-200 text-gray-400">
                <span class="text-sm font-medium">03</span>
              </div>
              <div class="ml-3">
                <div class="text-sm font-medium text-gray-500">Preview</div>
                <div class="text-xs text-gray-500">Penatibus eu quis ante.</div>
              </div>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'Circles',
      html: `
        <div class="w-full max-w-3xl mx-auto">
          <div class="flex items-center justify-center">
            <div class="w-8 h-8 flex items-center justify-center rounded-full bg-indigo-600 text-white">
              <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                <path d="M20 6L9 17L4 12" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </div>
            <div class="flex-1 h-0.5 bg-indigo-600"></div>
            <div class="w-8 h-8 flex items-center justify-center rounded-full bg-indigo-600 text-white">
              <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                <path d="M20 6L9 17L4 12" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </div>
            <div class="flex-1 h-0.5 bg-indigo-600"></div>
            <div class="w-8 h-8 flex items-center justify-center rounded-full border-2 border-indigo-600"></div>
            <div class="flex-1 h-0.5 bg-gray-200"></div>
            <div class="w-8 h-8 flex items-center justify-center rounded-full border-2 border-gray-200"></div>
            <div class="flex-1 h-0.5 bg-gray-200"></div>
            <div class="w-8 h-8 flex items-center justify-center rounded-full border-2 border-gray-200"></div>
          </div>
        </div>
      `
    },
    {
      name: 'Bullets and text',
      html: `
        <div class="w-full max-w-3xl mx-auto space-y-4">
          <div class="flex items-center">
            <div class="flex-shrink-0 w-5 h-5 rounded-full bg-indigo-600 flex items-center justify-center">
              <svg class="w-3 h-3 text-white" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                <path d="M20 6L9 17L4 12" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </div>
            <div class="ml-3 text-sm text-gray-900">Create account</div>
          </div>
          <div class="flex items-center">
            <div class="flex-shrink-0 w-5 h-5 rounded-full border-2 border-indigo-600"></div>
            <div class="ml-3 text-sm text-indigo-600">Profile information</div>
          </div>
          <div class="flex items-center">
            <div class="flex-shrink-0 w-5 h-5 rounded-full border-2 border-gray-200"></div>
            <div class="ml-3 text-sm text-gray-500">Theme</div>
          </div>
          <div class="flex items-center">
            <div class="flex-shrink-0 w-5 h-5 rounded-full border-2 border-gray-200"></div>
            <div class="ml-3 text-sm text-gray-500">Preview</div>
          </div>
        </div>
      `
    },
    {
      name: 'Circles with text',
      html: `
        <div class="w-full max-w-3xl mx-auto">
          <div class="relative">
            <div class="absolute left-8 h-full w-0.5 bg-gray-200"></div>
            <div class="space-y-8">
              <div class="flex items-center">
                <div class="flex-shrink-0 w-8 h-8 bg-indigo-600 rounded-full flex items-center justify-center">
                  <svg class="w-5 h-5 text-white" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                    <path d="M20 6L9 17L4 12" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </div>
                <div class="ml-4">
                  <div class="text-sm font-medium">Create account</div>
                  <div class="text-sm text-gray-500">Vitae sed mi luctus laoreet.</div>
                </div>
              </div>
              <div class="flex items-center">
                <div class="flex-shrink-0 w-8 h-8 border-2 border-indigo-600 rounded-full flex items-center justify-center"></div>
                <div class="ml-4">
                  <div class="text-sm font-medium text-indigo-600">Profile information</div>
                  <div class="text-sm text-gray-500">Cursus semper viverra facilisis et et some more.</div>
                </div>
              </div>
              <div class="flex items-center">
                <div class="flex-shrink-0 w-8 h-8 border-2 border-gray-200 rounded-full flex items-center justify-center"></div>
                <div class="ml-4">
                  <div class="text-sm font-medium text-gray-500">Business information</div>
                  <div class="text-sm text-gray-500">Penatibus eu quis ante.</div>
                </div>
              </div>
              <div class="flex items-center">
                <div class="flex-shrink-0 w-8 h-8 border-2 border-gray-200 rounded-full flex items-center justify-center"></div>
                <div class="ml-4">
                  <div class="text-sm font-medium text-gray-500">Theme</div>
                  <div class="text-sm text-gray-500">Faucibus nec enim leo et.</div>
                </div>
              </div>
              <div class="flex items-center">
                <div class="flex-shrink-0 w-8 h-8 border-2 border-gray-200 rounded-full flex items-center justify-center"></div>
                <div class="ml-4">
                  <div class="text-sm font-medium text-gray-500">Preview</div>
                  <div class="text-sm text-gray-500">Iusto et officia maiores porro ad non quas.</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      `
    },
    {
      name: 'Progress bar',
      html: `
        <div class="w-full max-w-3xl mx-auto">
          <div class="mb-4">
            <div class="text-sm text-gray-700">Migrating MySQL database...</div>
          </div>
          <div class="w-full bg-gray-200 rounded-full h-1.5 mb-4">
            <div class="bg-indigo-600 h-1.5 rounded-full" style="width: 45%"></div>
          </div>
          <div class="flex justify-between text-sm">
            <div class="text-indigo-600">Copying files</div>
            <div class="text-indigo-600">Migrating database</div>
            <div class="text-gray-500">Compiling assets</div>
            <div class="text-gray-500">Deployed</div>
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