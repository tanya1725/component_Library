<template>
  <div class="flex h-screen bg-gray-100 font-sans">
    <!-- Sidebar -->
    <aside class="w-64 bg-white shadow-md">
      <div class="p-4">
        <h1 class="text-2xl font-bold text-gray-800">Components</h1>
      </div>
      <nav class="mt-4">
        <ul>
          <li v-for="component in components" :key="component" class="mb-2">
            <button
              @click="selectComponent(component)"
              :class="[
                'w-full text-left px-4 py-2 text-sm font-medium transition-colors duration-150 ease-in-out',
                selectedComponent === component
                  ? 'bg-blue-500 text-white'
                  : 'text-gray-600 hover:bg-gray-100'
              ]"
            >
              {{ component }}
            </button>
          </li>
        </ul>
      </nav>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 overflow-x-hidden overflow-y-auto bg-gray-100">
      <div class="container mx-auto px-6 py-8">
        <h2 class="text-3xl font-bold text-gray-800 mb-6">{{ selectedComponent }} Variations</h2>
        
        <component :is="currentComponent" />
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import ButtonComponent from './ButtonComponent.vue'
import InputComponent from './InputComponent.vue'
import RadioComponent from './RadioComponent.vue'

const selectedComponent = ref('Button')
const components = ['Button', 'Input', 'Radio Groups']

const componentMap = {
  Button: ButtonComponent,
  Input: InputComponent,
  'Radio Groups': RadioComponent
}

const currentComponent = computed(() => componentMap[selectedComponent.value])

const selectComponent = (component) => {
  selectedComponent.value = component
}
</script>