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
  import { BarChart3, Shield, Zap, Code2, ArrowRight, CheckCircle, Users, Clock, Cloud, Settings, Lock, Bell } from 'lucide-vue-next'
  
  const showCode = ref({})
  
  const variations = [
    {
      name: 'Three Column Bento Grid',
      html: `
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <div class="md:col-span-2 md:row-span-2 bg-white rounded-2xl overflow-hidden shadow-lg">
          <div class="relative h-64">
            <img 
              src="/placeholder.svg?height=400&width=600"
              alt="Main Feature" 
              class="absolute inset-0 w-full h-full object-cover"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
            <div class="absolute bottom-4 left-4 right-4">
              <h3 class="text-2xl font-bold text-white mb-2">Analytics Dashboard</h3>
              <p class="text-white/90">Comprehensive data visualization and reporting tools</p>
            </div>
          </div>
          <div class="p-6">
            <div class="flex items-center gap-4 mb-4">
              <svg class="w-6 h-6 text-indigo-600" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="18" height="18" x="3" y="3" rx="2"/><path d="M3 9h18"/><path d="M15 14v3"/><path d="M9 14v6"/><path d="M21 9v12"/></svg>
              <span class="text-lg font-semibold">Real-time Metrics</span>
            </div>
            <p class="text-gray-600">Track your application's performance with our advanced analytics dashboard. Get insights into user behavior, system performance, and business metrics.</p>
          </div>
        </div>
        <div class="bg-white rounded-2xl overflow-hidden shadow-lg">
          <div class="relative h-48">
            <img 
              src="/placeholder.svg?height=200&width=300"
              alt="Team Collaboration" 
              class="absolute inset-0 w-full h-full object-cover"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
            <div class="absolute bottom-4 left-4 right-4">
              <h3 class="text-xl font-bold text-white">Team Collaboration</h3>
            </div>
          </div>
          <div class="p-4">
            <div class="flex items-center gap-3 mb-3">
              <svg class="w-5 h-5 text-indigo-600" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M22 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
              <span class="font-medium">Work Together</span>
            </div>
            <p class="text-gray-600 text-sm">Enable seamless collaboration between team members with real-time updates.</p>
          </div>
        </div>
        <div class="bg-white rounded-2xl overflow-hidden shadow-lg">
          <div class="relative h-48">
            <img 
              src="/placeholder.svg?height=200&width=300"
              alt="Performance Metrics" 
              class="absolute inset-0 w-full h-full object-cover"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
            <div class="absolute bottom-4 left-4 right-4">
              <h3 class="text-xl font-bold text-white">Performance Metrics</h3>
            </div>
          </div>
          <div class="p-4">
            <div class="flex items-center gap-3 mb-3">
              <svg class="w-5 h-5 text-indigo-600" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
              <span class="font-medium">Track Progress</span>
            </div>
            <p class="text-gray-600 text-sm">Monitor and optimize your application performance with detailed analytics.</p>
          </div>
        </div>
      </div>
      `
    },
    {
      name: 'Two Row Bento Grid on Dark',
      html: `
      <div class="bg-gray-900 p-6 rounded-lg">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div class="md:col-span-2 bg-gray-800 rounded-2xl overflow-hidden shadow-lg">
            <div class="relative h-64">
              <img 
                src="/placeholder.svg?height=400&width=600"
                alt="Dark Feature" 
                class="absolute inset-0 w-full h-full object-cover"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-gray-900/80 to-transparent"></div>
              <div class="absolute bottom-4 left-4 right-4">
                <h3 class="text-2xl font-bold text-white mb-2">Security Features</h3>
                <p class="text-gray-300">Enterprise-grade security for your applications</p>
              </div>
            </div>
            <div class="p-6">
              <div class="flex items-center gap-4 mb-4">
                <svg class="w-6 h-6 text-indigo-400" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
                <span class="text-lg font-semibold text-white">Advanced Protection</span>
              </div>
              <p class="text-gray-400">Implement robust security measures with our comprehensive suite of tools and features.</p>
            </div>
          </div>
          <div class="bg-gray-800 rounded-2xl overflow-hidden shadow-lg">
            <div class="p-6">
              <div class="flex items-center gap-3 mb-4">
                <svg class="w-6 h-6 text-indigo-400" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="18" height="11" x="3" y="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
                <h3 class="text-lg font-semibold text-white">Authentication</h3>
              </div>
              <p class="text-gray-400 mb-4">Secure user authentication and authorization systems.</p>
              <div class="flex items-center gap-2 text-indigo-400">
                <span class="text-sm font-medium">Learn more</span>
                <svg class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
              </div>
            </div>
          </div>
          <div class="bg-gray-800 rounded-2xl overflow-hidden shadow-lg">
            <div class="p-6">
              <div class="flex items-center gap-3 mb-4">
                <svg class="w-6 h-6 text-indigo-400" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
                <h3 class="text-lg font-semibold text-white">API Security</h3>
              </div>
              <p class="text-gray-400 mb-4">Protected API endpoints with industry-standard security.</p>
              <div class="flex items-center gap-2 text-indigo-400">
                <span class="text-sm font-medium">Learn more</span>
                <svg class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
              </div>
            </div>
          </div>
        </div>
      </div>
      `
    },
    {
      name: 'Two Row Bento Grid',
      html: `
      <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
        <div class="md:col-span-2 md:row-span-2 bg-white rounded-2xl overflow-hidden shadow-lg">
          <div class="relative h-72">
            <img 
              src="/placeholder.svg?height=400&width=600"
              alt="Feature" 
              class="absolute inset-0 w-full h-full object-cover"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
            <div class="absolute bottom-4 left-4 right-4">
              <h3 class="text-2xl font-bold text-white mb-2">Developer Experience</h3>
              <p class="text-white/90">Build faster with modern tools</p>
            </div>
          </div>
          <div class="p-6">
            <div class="flex items-center gap-4 mb-4">
              <svg class="w-6 h-6 text-indigo-600" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m18 16 4-4-4-4"/><path d="m6 8-4 4 4 4"/><path d="m14.5 4-5 16"/></svg>
              <span class="text-lg font-semibold">Modern Development</span>
            </div>
            <p class="text-gray-600 mb-4">Access a complete suite of development tools and resources designed to accelerate your workflow.</p>
            <div class="grid grid-cols-2 gap-4">
              <div class="flex items-center gap-2 text-sm text-gray-600">
                <svg class="w-4 h-4 text-green-500" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/><path d="m9 11 3 3L22 4"/></svg>
                <span>TypeScript Support</span>
              </div>
              <div class="flex items-center gap-2 text-sm text-gray-600">
                <svg class="w-4 h-4 text-green-500" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/><path d="m9 11 3 3L22 4"/></svg>
                <span>API Integration</span>
              </div>
              <div class="flex items-center gap-2 text-sm text-gray-600">
                <svg class="w-4 h-4 text-green-500" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/><path d="m9 11 3 3L22 4"/></svg>
                <span>Live Preview</span>
              </div>
              <div class="flex items-center gap-2 text-sm text-gray-600">
                <svg class="w-4 h-4 text-green-500" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/><path d="m9 11 3 3L22 4"/></svg>
                <span>Plugin System</span>
              </div>
            </div>
          </div>
        </div>
        <div class="bg-white rounded-2xl overflow-hidden shadow-lg">
          <div class="p-6">
            <div class="flex items-center gap-3 mb-4">
              <svg class="w-6 h-6 text-indigo-600" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m13 2-2 2.5h3L12 7"/><path d="M12 22v-3"/><path d="M12 17v-2"/><path d="M12 11V9"/><path d="M3 5v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V5a2 2 0 0 0-2-2H5a2 2 0 0 0-2 2Z"/></svg>
              <h3 class="text-lg font-semibold">Quick Setup</h3>
            </div>
            <p class="text-gray-600 mb-4">Get started in minutes with our streamlined setup process.</p>
            <div class="flex items-center gap-2 text-indigo-600">
              <span class="text-sm font-medium">Start now</span>
              <svg class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
            </div>
          </div>
        </div>
        <div class="bg-white rounded-2xl overflow-hidden shadow-lg">
          <div class="p-6">
            <div class="flex items-center gap-3 mb-4">
              <svg class="w-6 h-6 text-indigo-600" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"/></svg>
              <h3 class="text-lg font-semibold">Configuration</h3>
            </div>
            <p class="text-gray-600 mb-4">Customize every aspect of your development environment.</p>
            <div class="flex items-center gap-2 text-indigo-600">
              <span class="text-sm font-medium">Configure</span>
              <svg class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
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