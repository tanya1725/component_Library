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
import { Users, Target, Award, ChevronRight, Calendar, Clock } from 'lucide-vue-next'

const showCode = ref({})

const variations = [
  {
    name: 'With image tiles',
    html: `
      <div class="bg-white">
        <div class="max-w-7xl mx-auto py-16 px-4 sm:py-24 sm:px-6 lg:px-8">
          <div class="text-center">
            <h2 class="text-base font-semibold text-indigo-600 tracking-wide uppercase">About Us</h2>
            <p class="mt-1 text-4xl font-extrabold text-gray-900 sm:text-5xl sm:tracking-tight lg:text-6xl">Our Company Story</p>
            <p class="max-w-xl mt-5 mx-auto text-xl text-gray-500">Learn about our journey, our team, and our mission.</p>
          </div>
          <div class="mt-16">
            <div class="grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3">
              <div class="pt-6">
                <div class="flow-root bg-gray-50 rounded-lg px-6 pb-8">
                  <div class="-mt-6">
                    <div>
                      <span class="inline-flex items-center justify-center p-3 bg-indigo-500 rounded-md shadow-lg">
                        <Users class="h-6 w-6 text-white" aria-hidden="true" />
                      </span>
                    </div>
                    <h3 class="mt-8 text-lg font-medium text-gray-900 tracking-tight">Our Team</h3>
                    <p class="mt-5 text-base text-gray-500">
                      Meet the passionate individuals behind our success. Our diverse team brings a wealth of experience and creativity to every project.
                    </p>
                  </div>
                </div>
              </div>
              <div class="pt-6">
                <div class="flow-root bg-gray-50 rounded-lg px-6 pb-8">
                  <div class="-mt-6">
                    <div>
                      <span class="inline-flex items-center justify-center p-3 bg-indigo-500 rounded-md shadow-lg">
                        <Target class="h-6 w-6 text-white" aria-hidden="true" />
                      </span>
                    </div>
                    <h3 class="mt-8 text-lg font-medium text-gray-900 tracking-tight">Our Mission</h3>
                    <p class="mt-5 text-base text-gray-500">
                      We're on a mission to revolutionize the industry through innovation, quality, and customer-centric solutions.
                    </p>
                  </div>
                </div>
              </div>
              <div class="pt-6">
                <div class="flow-root bg-gray-50 rounded-lg px-6 pb-8">
                  <div class="-mt-6">
                    <div>
                      <span class="inline-flex items-center justify-center p-3 bg-indigo-500 rounded-md shadow-lg">
                        <Award class="h-6 w-6 text-white" aria-hidden="true" />
                      </span>
                    </div>
                    <h3 class="mt-8 text-lg font-medium text-gray-900 tracking-tight">Our Values</h3>
                    <p class="mt-5 text-base text-gray-500">
                      Integrity, innovation, and excellence are the core values that guide our every decision and action.
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    `
  },
  {
    name: 'With timeline and stats',
    html: `
      <div class="bg-white">
        <div class="max-w-7xl mx-auto py-16 px-4 sm:py-24 sm:px-6 lg:px-8">
          <div class="text-center">
            <h2 class="text-base font-semibold text-indigo-600 tracking-wide uppercase">Our Journey</h2>
            <p class="mt-1 text-4xl font-extrabold text-gray-900 sm:text-5xl sm:tracking-tight lg:text-6xl">Milestones & Achievements</p>
          </div>
          <div class="mt-16">
            <div class="flow-root">
              <ul role="list" class="-mb-8">
                <li>
                  <div class="relative pb-8">
                    <span class="absolute top-4 left-4 -ml-px h-full w-0.5 bg-gray-200" aria-hidden="true"></span>
                    <div class="relative flex space-x-3">
                      <div>
                        <span class="h-8 w-8 rounded-full bg-indigo-500 flex items-center justify-center ring-8 ring-white">
                          <Calendar class="h-5 w-5 text-white" aria-hidden="true" />
                        </span>
                      </div>
                      <div class="min-w-0 flex-1 pt-1.5 flex justify-between space-x-4">
                        <div>
                          <p class="text-sm text-gray-500">Founded the company</p>
                        </div>
                        <div class="text-right text-sm whitespace-nowrap text-gray-500">
                          <time datetime="2020-09-20">Sep 2020</time>
                        </div>
                      </div>
                    </div>
                  </div>
                </li>
                <li>
                  <div class="relative pb-8">
                    <span class="absolute top-4 left-4 -ml-px h-full w-0.5 bg-gray-200" aria-hidden="true"></span>
                    <div class="relative flex space-x-3">
                      <div>
                        <span class="h-8 w-8 rounded-full bg-indigo-500 flex items-center justify-center ring-8 ring-white">
                          <Users class="h-5 w-5 text-white" aria-hidden="true" />
                        </span>
                      </div>
                      <div class="min-w-0 flex-1 pt-1.5 flex justify-between space-x-4">
                        <div>
                          <p class="text-sm text-gray-500">Reached 100 employees</p>
                        </div>
                        <div class="text-right text-sm whitespace-nowrap text-gray-500">
                          <time datetime="2021-06-12">Jun 2021</time>
                        </div>
                      </div>
                    </div>
                  </div>
                </li>
                <li>
                  <div class="relative pb-8">
                    <div class="relative flex space-x-3">
                      <div>
                        <span class="h-8 w-8 rounded-full bg-indigo-500 flex items-center justify-center ring-8 ring-white">
                          <Award class="h-5 w-5 text-white" aria-hidden="true" />
                        </span>
                      </div>
                      <div class="min-w-0 flex-1 pt-1.5 flex justify-between space-x-4">
                        <div>
                          <p class="text-sm text-gray-500">Won Industry Innovation Award</p>
                        </div>
                        <div class="text-right text-sm whitespace-nowrap text-gray-500">
                          <time datetime="2022-03-15">Mar 2022</time>
                        </div>
                      </div>
                    </div>
                  </div>
                </li>
              </ul>
            </div>
          </div>
          <div class="mt-16">
            <h3 class="text-lg font-medium text-gray-900">Company Statistics</h3>
            <dl class="mt-5 grid grid-cols-1 gap-5 sm:grid-cols-3">
              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">Total Customers</dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">12,000+</dd>
              </div>
              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">Countries Served</dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">50+</dd>
              </div>
              <div class="px-4 py-5 bg-white shadow rounded-lg overflow-hidden sm:p-6">
                <dt class="text-sm font-medium text-gray-500 truncate">Team Members</dt>
                <dd class="mt-1 text-3xl font-semibold text-gray-900">200+</dd>
              </div>
            </dl>
          </div>
        </div>
      </div>
    `
  },
  {
    name: 'Dark theme',
    html: `
      <div class="bg-gray-900">
        <div class="max-w-7xl mx-auto py-16 px-4 sm:py-24 sm:px-6 lg:px-8">
          <div class="text-center">
            <h2 class="text-base font-semibold text-indigo-400 tracking-wide uppercase">About Us</h2>
            <p class="mt-1 text-4xl font-extrabold text-white sm:text-5xl sm:tracking-tight lg:text-6xl">Innovating for Tomorrow</p>
            <p class="max-w-xl mt-5 mx-auto text-xl text-gray-400">Discover our passion for technology and commitment to excellence.</p>
          </div>
          <div class="mt-16">
            <div class="grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3">
              <div class="pt-6">
                <div class="flow-root bg-gray-800 rounded-lg px-6 pb-8">
                  <div class="-mt-6">
                    <div>
                      <span class="inline-flex items-center justify-center p-3 bg-indigo-500 rounded-md shadow-lg">
                        <Users class="h-6 w-6 text-white" aria-hidden="true" />
                      </span>
                    </div>
                    <h3 class="mt-8 text-lg font-medium text-white tracking-tight">Our Team</h3>
                    <p class="mt-5 text-base text-gray-400">
                      A diverse group of experts dedicated to pushing the boundaries of what's possible.
                    </p>
                  </div>
                </div>
              </div>
              <div class="pt-6">
                <div class="flow-root bg-gray-800 rounded-lg px-6 pb-8">
                  <div class="-mt-6">
                    <div>
                      <span class="inline-flex items-center justify-center p-3 bg-indigo-500 rounded-md shadow-lg">
                        <Target class="h-6 w-6 text-white" aria-hidden="true" />
                      </span>
                    </div>
                    <h3 class="mt-8 text-lg font-medium text-white tracking-tight">Our Mission</h3>
                    <p class="mt-5 text-base text-gray-400">
                      To create innovative solutions that transform industries and improve lives.
                    </p>
                  </div>
                </div>
              </div>
              <div class="pt-6">
                <div class="flow-root bg-gray-800 rounded-lg px-6 pb-8">
                  <div class="-mt-6">
                    <div>
                      <span class="inline-flex items-center justify-center p-3 bg-indigo-500 rounded-md shadow-lg">
                        <Clock class="h-6 w-6 text-white" aria-hidden="true" />
                      </span>
                    </div>
                    <h3 class="mt-8 text-lg font-medium text-white tracking-tight">Our Future</h3>
                    <p class="mt-5 text-base text-gray-400">
                      Committed to shaping a better tomorrow through continuous innovation and sustainability.
                    </p>
                  </div>
                </div>
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
/* Add any additional styles here if needed */
</style>