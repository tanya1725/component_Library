<template>
    <div class="space-y-4">
        <div v-for="(variation, index) in variations" :key="index" class="bg-white rounded-lg shadow-md w-full">
            <div class="p-4 bg-gray-50 border-b">
                <h3 class="text-lg font-semibold text-gray-800">{{ variation.name }}</h3>
            </div>
            <div class="p-4">
                <div class="mb-4">
                    <div class="p-4 bg-gray-100 rounded-md">
                        <!-- Card Preview -->
                        <div v-html="variation.component"></div>
                    </div>
                </div>
                <div>
                    <button @click="toggleCode(index)"
                        class="px-4 py-2 text-sm font-medium text-blue-600 bg-blue-100 rounded-md hover:bg-blue-200 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2">
                        {{ showCode[index] ? 'Hide Code' : 'Show Code' }}
                    </button>
                </div>
                <div v-show="showCode[index]" class="mt-4">
                    <pre class="p-4 bg-gray-800 rounded-md overflow-x-auto">
              <code class="text-sm text-white">{{ variation.code }}</code>
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
        name: 'Basic card',
        component: `
        <div class="bg-white rounded-lg shadow-sm">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>
      `,
        html: `
        <div class="bg-white rounded-lg shadow-sm">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>`
    },
    {
        name: 'Card, edge-to-edge on mobile',
        component: `
        <div class="bg-white shadow-sm sm:rounded-lg -mx-4 sm:mx-0">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>
      `,
        html: `
        <div class="bg-white shadow-sm sm:rounded-lg -mx-4 sm:mx-0">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>`
    },
    {
        name: 'Card with header',
        component: `
        <div class="bg-white rounded-lg shadow-sm divide-y divide-gray-200">
          <div class="p-6">
            <div class="h-12 rounded border-2 border-dashed border-gray-200"></div>
          </div>
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>
      `,
        html: `
        <div class="bg-white rounded-lg shadow-sm divide-y divide-gray-200">
          <div class="p-6">
            <div class="h-12 rounded border-2 border-dashed border-gray-200"></div>
          </div>
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>`
    },
    {
        name: 'Card with footer',
        component: `
        <div class="bg-white rounded-lg shadow-sm divide-y divide-gray-200">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
          <div class="p-6">
            <div class="h-12 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>
      `,
        html: `
        <div class="bg-white rounded-lg shadow-sm divide-y divide-gray-200">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
          <div class="p-6">
            <div class="h-12 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>`
    },
    {
        name: 'Card with header and footer',
        component: `
        <div class="bg-white rounded-lg shadow-sm divide-y divide-gray-200">
          <div class="p-6">
            <div class="h-12 rounded border-2 border-dashed border-gray-200"></div>
          </div>
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
          <div class="p-6">
            <div class="h-12 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>
      `,
        html: `
        <div class="bg-white rounded-lg shadow-sm divide-y divide-gray-200">
          <div class="p-6">
            <div class="h-12 rounded border-2 border-dashed border-gray-200"></div>
          </div>
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
          <div class="p-6">
            <div class="h-12 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>`
    },
    {
        name: 'Card with gray footer',
        component: `
        <div class="bg-white rounded-lg shadow-sm divide-y divide-gray-200">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
          <div class="p-6 bg-gray-50">
            <div class="h-12 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>
      `,
        html: `
        <div class="bg-white rounded-lg shadow-sm divide-y divide-gray-200">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
          <div class="p-6 bg-gray-50">
            <div class="h-12 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>`
    },
    {
        name: 'Card with gray body',
        component: `
        <div class="bg-white rounded-lg shadow-sm">
          <div class="p-6 bg-gray-50">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>
      `,
        html: `
        <div class="bg-white rounded-lg shadow-sm">
          <div class="p-6 bg-gray-50">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>`
    },
    {
        name: 'Well',
        component: `
        <div class="bg-white rounded-lg shadow-sm ring-1 ring-gray-900/5">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>
      `,
        html: `
        <div class="bg-white rounded-lg shadow-sm ring-1 ring-gray-900/5">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>`
    },
    {
        name: 'Well on gray',
        component: `
        <div class="bg-gray-50 rounded-lg shadow-sm ring-1 ring-gray-900/5">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>
      `,
        html: `
        <div class="bg-gray-50 rounded-lg shadow-sm ring-1 ring-gray-900/5">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>`
    },
    {
        name: 'Well, edge-to-edge on mobile',
        component: `
        <div class="bg-white shadow-sm ring-1 ring-gray-900/5 -mx-4 sm:mx-0 sm:rounded-lg">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>
      `,
        html: `
        <div class="bg-white shadow-sm ring-1 ring-gray-900/5 -mx-4 sm:mx-0 sm:rounded-lg">
          <div class="p-6">
            <div class="h-48 rounded border-2 border-dashed border-gray-200"></div>
          </div>
        </div>`
    }
]

const toggleCode = (index) => {
    showCode.value[index] = !showCode.value[index]
}
</script>