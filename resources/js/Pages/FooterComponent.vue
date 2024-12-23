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
  
  const showCode = ref({})
  
  const variations = [
    {
      name: '4-column with company mission',
      html: `
        <footer class="bg-white">
          <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
            <div class="xl:grid xl:grid-cols-3 xl:gap-8">
              <div class="grid grid-cols-2 gap-8 xl:col-span-2">
                <div class="md:grid md:grid-cols-2 md:gap-8">
                  <div>
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Solutions</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Marketing</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Analytics</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Commerce</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Insights</a></li>
                    </ul>
                  </div>
                  <div class="mt-12 md:mt-0">
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Support</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Pricing</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Documentation</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Guides</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">API Status</a></li>
                    </ul>
                  </div>
                </div>
                <div class="md:grid md:grid-cols-2 md:gap-8">
                  <div>
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Company</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">About</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Blog</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Jobs</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Press</a></li>
                    </ul>
                  </div>
                  <div class="mt-12 md:mt-0">
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Legal</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Privacy</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Terms</a></li>
                    </ul>
                  </div>
                </div>
              </div>
              <div class="mt-8 xl:mt-0">
                <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Our Mission</h3>
                <p class="mt-4 text-base text-gray-500">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean euismod bibendum laoreet. Proin gravida dolor sit amet lacus accumsan et viverra justo commodo.
                </p>
              </div>
            </div>
            <div class="mt-8 border-t border-gray-200 pt-8">
              <p class="text-base text-gray-400 xl:text-center">&copy; 2023 Your Company, Inc. All rights reserved.</p>
            </div>
          </div>
        </footer>
      `
    },
    {
    name: '4-column with company mission dark',
    html: `
      <footer class="bg-white dark:bg-gray-800">
        <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
          <div class="xl:grid xl:grid-cols-3 xl:gap-8">
            <div class="grid grid-cols-2 gap-8 xl:col-span-2">
              <div class="md:grid md:grid-cols-2 md:gap-8">
                <div>
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Solutions</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Marketing</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Analytics</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Commerce</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Insights</a></li>
                  </ul>
                </div>
                <div class="mt-12 md:mt-0">
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Support</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Pricing</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Documentation</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Guides</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">API Status</a></li>
                  </ul>
                </div>
              </div>
              <div class="md:grid md:grid-cols-2 md:gap-8">
                <div>
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Company</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">About</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Blog</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Jobs</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Press</a></li>
                  </ul>
                </div>
                <div class="mt-12 md:mt-0">
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Legal</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Privacy</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Terms</a></li>
                  </ul>
                </div>
              </div>
            </div>
            <div class="mt-8 xl:mt-0">
              <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Our Mission</h3>
              <p class="mt-4 text-base text-gray-500 dark:text-gray-400">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean euismod bibendum laoreet. Proin gravida dolor sit amet lacus accumsan et viverra justo commodo.
              </p>
            </div>
          </div>
          <div class="mt-8 border-t border-gray-200 dark:border-gray-700 pt-8">
            <p class="text-base text-gray-400 xl:text-center">&copy; 2023 Your Company, Inc. All rights reserved.</p>
          </div>
        </div>
      </footer>
    `
  },
    {
      name: '4-column with call-to-action',
      html: `
        <footer class="bg-white">
          <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
            <div class="xl:grid xl:grid-cols-3 xl:gap-8">
              <div class="grid grid-cols-2 gap-8 xl:col-span-2">
                <div class="md:grid md:grid-cols-2 md:gap-8">
                  <div>
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Solutions</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Marketing</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Analytics</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Commerce</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Insights</a></li>
                    </ul>
                  </div>
                  <div class="mt-12 md:mt-0">
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Support</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Pricing</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Documentation</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Guides</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">API Status</a></li>
                    </ul>
                  </div>
                </div>
                <div class="md:grid md:grid-cols-2 md:gap-8">
                  <div>
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Company</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">About</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Blog</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Jobs</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Press</a></li>
                    </ul>
                  </div>
                  <div class="mt-12 md:mt-0">
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Legal</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Privacy</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Terms</a></li>
                    </ul>
                  </div>
                </div>
              </div>
              <div class="mt-8 xl:mt-0">
                <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Subscribe to our newsletter</h3>
                <p class="mt-4 text-base text-gray-500">
                  The latest news, articles, and resources, sent to your inbox weekly.
                </p>
                <form class="mt-4 sm:flex sm:max-w-md">
                  <label for="email-address" class="sr-only">Email address</label>
                  <input type="email" name="email-address" id="email-address" autocomplete="email" required class="appearance-none min-w-0 w-full bg-white border border-gray-300 rounded-md shadow-sm py-2 px-4 text-base text-gray-900 placeholder-gray-500 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:placeholder-gray-400" placeholder="Enter your email">
                  <div class="mt-3 rounded-md sm:mt-0 sm:ml-3 sm:flex-shrink-0">
                    <button type="submit" class="w-full bg-indigo-600 flex items-center justify-center border border-transparent rounded-md py-2 px-4 text-base font-medium text-white hover:bg-indigo-700 focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                      Subscribe
                    </button>
                  </div>
                </form>
              </div>
            </div>
            <div class="mt-8 border-t border-gray-200 pt-8">
              <p class="text-base text-gray-400 xl:text-center">&copy; 2023 Your Company, Inc. All rights reserved.</p>
            </div>
          </div>
        </footer>
      `
    },
    {
      name: '4-column simple',
      html: `
        <footer class="bg-white">
          <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
            <div class="xl:grid xl:grid-cols-3 xl:gap-8">
              <div class="grid grid-cols-2 gap-8 xl:col-span-2">
                <div class="md:grid md:grid-cols-2 md:gap-8">
                  <div>
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Solutions</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Marketing</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Analytics</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Commerce</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Insights</a></li>
                    </ul>
                  </div>
                  <div class="mt-12 md:mt-0">
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Support</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Pricing</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Documentation</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Guides</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">API Status</a></li>
                    </ul>
                  </div>
                </div>
                <div class="md:grid md:grid-cols-2 md:gap-8">
                  <div>
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Company</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">About</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Blog</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Jobs</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Press</a></li>
                    </ul>
                  </div>
                  <div class="mt-12 md:mt-0">
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Legal</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Privacy</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Terms</a></li>
                    </ul>
                  </div>
                </div>
              </div>
              <div class="mt-8 xl:mt-0">
                <img class="h-10" src="/placeholder.svg?height=40&width=120" alt="Company logo">
                <p class="mt-4 text-base text-gray-500">
                  Making the world a better place through constructing elegant hierarchies.
                </p>
              </div>
            </div>
            <div class="mt-8 border-t border-gray-200 pt-8">
              <p class="text-base text-gray-400 xl:text-center">&copy; 2023 Your Company, Inc. All rights reserved.</p>
            </div>
          </div>
        </footer>
      `
    },
    {
      name: '4-column with newsletter',
      html: `
        <footer class="bg-white">
          <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
            <div class="xl:grid xl:grid-cols-3 xl:gap-8">
              <div class="grid grid-cols-2 gap-8 xl:col-span-2">
                <div class="md:grid md:grid-cols-2 md:gap-8">
                  <div>
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Solutions</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Marketing</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Analytics</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Commerce</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Insights</a></li>
                    </ul>
                  </div>
                  <div class="mt-12 md:mt-0">
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Support</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Pricing</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Documentation</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Guides</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">API Status</a></li>
                    </ul>
                  </div>
                </div>
                <div class="md:grid md:grid-cols-2 md:gap-8">
                  <div>
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Company</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">About</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Blog</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Jobs</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Press</a></li>
                    </ul>
                  </div>
                  <div class="mt-12 md:mt-0">
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Legal</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Privacy</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Terms</a></li>
                    </ul>
                  </div>
                </div>
              </div>
              <div class="mt-8 xl:mt-0">
                <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Subscribe to our newsletter</h3>
                <p class="mt-4 text-base text-gray-500">
                  The latest news, articles, and resources, sent to your inbox weekly.
                </p>
                <form class="mt-4 sm:flex sm:max-w-md">
                  <label for="email-address" class="sr-only">Email address</label>
                  <input type="email" name="email-address" id="email-address" autocomplete="email" required class="appearance-none min-w-0 w-full bg-white border border-gray-300 rounded-md shadow-sm py-2 px-4 text-base text-gray-900 placeholder-gray-500 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:placeholder-gray-400" placeholder="Enter your email">
                  <div class="mt-3 rounded-md sm:mt-0 sm:ml-3 sm:flex-shrink-0">
                    <button type="submit" class="w-full bg-indigo-600 flex items-center justify-center border border-transparent rounded-md py-2 px-4 text-base font-medium text-white hover:bg-indigo-700 focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                      Subscribe
                    </button>
                  </div>
                </form>
              </div>
            </div>
            <div class="mt-8 border-t border-gray-200 pt-8">
              <p class="text-base text-gray-400 xl:text-center">&copy; 2023 Your Company, Inc. All rights reserved.</p>
            </div>
          </div>
        </footer>
      `
    },
    {
    name: '4-column with newsletter',
    html: `
      <footer class="bg-white dark:bg-gray-800">
        <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
          <div class="xl:grid xl:grid-cols-3 xl:gap-8">
            <div class="grid grid-cols-2 gap-8 xl:col-span-2">
              <div class="md:grid md:grid-cols-2 md:gap-8">
                <div>
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Solutions</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Marketing</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Analytics</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Commerce</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Insights</a></li>
                  </ul>
                </div>
                <div class="mt-12 md:mt-0">
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Support</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Pricing</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Documentation</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Guides</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">API Status</a></li>
                  </ul>
                </div>
              </div>
              <div class="md:grid md:grid-cols-2 md:gap-8">
                <div>
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Company</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">About</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Blog</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Jobs</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Press</a></li>
                  </ul>
                </div>
                <div class="mt-12 md:mt-0">
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Legal</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Privacy</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Terms</a></li>
                  </ul>
                </div>
              </div>
            </div>
            <div class="mt-8 xl:mt-0">
              <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Subscribe to our newsletter</h3>
              <p class="mt-4 text-base text-gray-500 dark:text-gray-400">
                The latest news, articles, and resources, sent to your inbox weekly.
              </p>
              <form class="mt-4 sm:flex sm:max-w-md">
                <label for="email-address" class="sr-only">Email address</label>
                <input type="email" name="email-address" id="email-address" autocomplete="email" required class="appearance-none min-w-0 w-full bg-white dark:bg-gray-700 border border-gray-300 dark:border-gray-600 rounded-md shadow-sm py-2 px-4 text-base text-gray-900 dark:text-white placeholder-gray-500 dark:placeholder-gray-400 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:placeholder-gray-400 dark:focus:ring-indigo-600 dark:focus:border-indigo-600" placeholder="Enter your email">
                <div class="mt-3 rounded-md sm:mt-0 sm:ml-3 sm:flex-shrink-0">
                  <button type="submit" class="w-full bg-indigo-600 flex items-center justify-center border border-transparent rounded-md py-2 px-4 text-base font-medium text-white hover:bg-indigo-700 focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 dark:bg-indigo-500 dark:hover:bg-indigo-600 dark:focus:ring-offset-gray-800">
                    Subscribe
                  </button>
                </div>
              </form>
            </div>
          </div>
          <div class="mt-8 border-t border-gray-200 dark:border-gray-700 pt-8">
            <p class="text-base text-gray-400 xl:text-center">&copy; 2023 Your Company, Inc. All rights reserved.</p>
          </div>
        </div>
      </footer>
    `
  },
    {
      name: '4-column with newsletter below',
      html: `
        <footer class="bg-white">
          <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
            <div class="xl:grid xl:grid-cols-3 xl:gap-8">
              <div class="grid grid-cols-2 gap-8 xl:col-span-2">
                <div class="md:grid md:grid-cols-2 md:gap-8">
                  <div>
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Solutions</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Marketing</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Analytics</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Commerce</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Insights</a></li>
                    </ul>
                  </div>
                  <div class="mt-12 md:mt-0">
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Support</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Pricing</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Documentation</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Guides</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">API Status</a></li>
                    </ul>
                  </div>
                </div>
                <div class="md:grid md:grid-cols-2 md:gap-8">
                  <div>
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Company</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">About</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Blog</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Jobs</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Press</a></li>
                    </ul>
                  </div>
                  <div class="mt-12 md:mt-0">
                    <h3 class="text-sm font-semibold text-gray-400 tracking-wider uppercase">Legal</h3>
                    <ul class="mt-4 space-y-4">
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Privacy</a></li>
                      <li><a href="#" class="text-base text-gray-500 hover:text-gray-900">Terms</a></li>
                    </ul>
                  </div>
                </div>
              </div>
              <div class="mt-8 xl:mt-0">
                <img class="h-10" src="/placeholder.svg?height=40&width=120" alt="Company logo">
                <p class="mt-4 text-base text-gray-500">
                  Making the world a better place through constructing elegant hierarchies.
                </p>
              </div>
            </div>
            <div class="mt-8 border-t border-gray-200 pt-8 md:flex md:items-center md:justify-between">
              <div class="flex space-x-6 md:order-2">
                <a href="#" class="text-gray-400 hover:text-gray-500">
                  <span class="sr-only">Facebook</span>
                  <Facebook class="h-6 w-6" />
                </a>
                <a href="#" class="text-gray-400 hover:text-gray-500">
                  <span class="sr-only">Instagram</span>
                  <Instagram class="h-6 w-6" />
                </a>
                <a href="#" class="text-gray-400 hover:text-gray-500">
                  <span class="sr-only">Twitter</span>
                  <Twitter class="h-6 w-6" />
                </a>
                <a href="#" class="text-gray-400 hover:text-gray-500">
                  <span class="sr-only">GitHub</span>
                  <GitHub class="h-6 w-6" />
                </a>
              </div>
              <p class="mt-8 text-base text-gray-400 md:mt-0 md:order-1">
                &copy; 2023 Your Company, Inc. All rights reserved.
              </p>
            </div>
          </div>
          <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
            <h2 class="text-3xl font-extrabold text-gray-900 sm:text-4xl">
              <span class="block">Want product news and updates?</span>
              <span class="block text-indigo-600">Sign up for our newsletter.</span>
            </h2>
            <form class="mt-8 sm:flex">
              <label for="email-address" class="sr-only">Email address</label>
              <input id="email-address" name="email" type="email" autocomplete="email" required class="w-full px-5 py-3 placeholder-gray-500 focus:ring-indigo-500 focus:border-indigo-500 sm:max-w-xs border-gray-300 rounded-md" placeholder="Enter your email">
              <div class="mt-3 rounded-md shadow sm:mt-0 sm:ml-3 sm:flex-shrink-0">
                <button type="submit" class="w-full flex items-center justify-center px-5 py-3 border border-transparent text-base font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                  Notify me
                </button>
              </div>
            </form>
          </div>
        </footer>
      `
    },
    {
    name: '4-column with newsletter below',
    html: `
      <footer class="bg-white dark:bg-gray-800">
        <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
          <div class="xl:grid xl:grid-cols-3 xl:gap-8">
            <div class="grid grid-cols-2 gap-8 xl:col-span-2">
              <div class="md:grid md:grid-cols-2 md:gap-8">
                <div>
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Solutions</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Marketing</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Analytics</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Commerce</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Insights</a></li>
                  </ul>
                </div>
                <div class="mt-12 md:mt-0">
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Support</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Pricing</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Documentation</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Guides</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">API Status</a></li>
                  </ul>
                </div>
              </div>
              <div class="md:grid md:grid-cols-2 md:gap-8">
                <div>
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Company</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">About</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Blog</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Jobs</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Press</a></li>
                  </ul>
                </div>
                <div class="mt-12 md:mt-0">
                  <h3 class="text-sm font-semibold text-gray-400 dark:text-gray-300 tracking-wider uppercase">Legal</h3>
                  <ul class="mt-4 space-y-4">
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Privacy</a></li>
                    <li><a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">Terms</a></li>
                  </ul>
                </div>
              </div>
            </div>
            <div class="mt-8 xl:mt-0">
              <img class="h-10" src="/placeholder.svg?height=40&width=120" alt="Company logo">
              <p class="mt-4 text-base text-gray-500 dark:text-gray-400">
                Making the world a better place through constructing elegant hierarchies.
              </p>
            </div>
          </div>
          <div class="mt-8 border-t border-gray-200 dark:border-gray-700 pt-8 md:flex md:items-center md:justify-between">
            <div class="flex space-x-6 md:order-2">
              <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
                <span class="sr-only">Facebook</span>
                <Facebook class="h-6 w-6" />
              </a>
              <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
                <span class="sr-only">Instagram</span>
                <Instagram class="h-6 w-6" />
              </a>
              <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
                <span class="sr-only">Twitter</span>
                <Twitter class="h-6 w-6" />
              </a>
              <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
                <span class="sr-only">GitHub</span>
                <Github class="h-6 w-6" />
              </a>
            </div>
            <p class="mt-8 text-base text-gray-400 md:mt-0 md:order-1">
              &copy; 2023 Your Company, Inc. All rights reserved.
            </p>
          </div>
        </div>
        <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
          <h2 class="text-3xl font-extrabold text-gray-900 dark:text-white sm:text-4xl">
            <span class="block">Want product news and updates?</span>
            <span class="block text-indigo-600 dark:text-indigo-400">Sign up for our newsletter.</span>
          </h2>
          <form class="mt-8 sm:flex">
            <label for="email-address" class="sr-only">Email address</label>
            <input id="email-address" name="email" type="email" autocomplete="email" required class="w-full px-5 py-3 placeholder-gray-500 focus:ring-indigo-500 focus:border-indigo-500 sm:max-w-xs border-gray-300 rounded-md dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-indigo-600 dark:focus:border-indigo-600" placeholder="Enter your email">
            <div class="mt-3 rounded-md shadow sm:mt-0 sm:ml-3 sm:flex-shrink-0">
              <button type="submit" class="w-full flex items-center justify-center px-5 py-3 border border-transparent text-base font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 dark:bg-indigo-500 dark:hover:bg-indigo-600 dark:focus:ring-offset-gray-800">
                Notify me
              </button>
            </div>
          </form>
        </div>
      </footer>
    `
  },
    {
      name: 'Simple centered',
      html: `
        <footer class="bg-white">
          <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:px-8">
            <nav class="-mx-5 -my-2 flex flex-wrap justify-center" aria-label="Footer">
              <div class="px-5 py-2">
                <a href="#" class="text-base text-gray-500 hover:text-gray-900">
                  About
                </a>
              </div>
              <div class="px-5 py-2">
                <a href="#" class="text-base text-gray-500 hover:text-gray-900">
                  Blog
                </a>
              </div>
              <div class="px-5 py-2">
                <a href="#" class="text-base text-gray-500 hover:text-gray-900">
                  Jobs
                </a>
              </div>
              <div class="px-5 py-2">
                <a href="#" class="text-base text-gray-500 hover:text-gray-900">
                  Press
                </a>
              </div>
              <div class="px-5 py-2">
                <a href="#" class="text-base text-gray-500 hover:text-gray-900">
                  Accessibility
                </a>
              </div>
              <div class="px-5 py-2">
                <a href="#" class="text-base text-gray-500 hover:text-gray-900">
                  Partners
                </a>
              </div>
            </nav>
            <div class="mt-8 flex justify-center space-x-6">
              <a href="#" class="text-gray-400 hover:text-gray-500">
                <span class="sr-only">Facebook</span>
                <Facebook class="h-6 w-6" />
              </a>
              <a href="#" class="text-gray-400 hover:text-gray-500">
                <span class="sr-only">Instagram</span>
                <Instagram class="h-6 w-6" />
              </a>
              <a href="#" class="text-gray-400 hover:text-gray-500">
                <span class="sr-only">Twitter</span>
                <Twitter class="h-6 w-6" />
              </a>
              <a href="#" class="text-gray-400 hover:text-gray-500">
                <span class="sr-only">GitHub</span>
                <GitHub class="h-6 w-6" />
              </a>
            </div>
            <p class="mt-8 text-center text-base text-gray-400">
              &copy; 2023 Your Company, Inc. All rights reserved.
            </p>
          </div>
        </footer>
      `
    },
    {
    name: 'Simple centered',
    html: `
      <footer class="bg-white dark:bg-gray-800">
        <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:px-8">
          <nav class="-mx-5 -my-2 flex flex-wrap justify-center" aria-label="Footer">
            <div class="px-5 py-2">
              <a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">
                About
              </a>
            </div>
            <div class="px-5 py-2">
              <a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">
                Blog
              </a>
            </div>
            <div class="px-5 py-2">
              <a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">
                Jobs
              </a>
            </div>
            <div class="px-5 py-2">
              <a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">
                Press
              </a>
            </div>
            <div class="px-5 py-2">
              <a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">
                Accessibility
              </a>
            </div>
            <div class="px-5 py-2">
              <a href="#" class="text-base text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white">
                Partners
              </a>
            </div>
          </nav>
          <div class="mt-8 flex justify-center space-x-6">
            <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
              <span class="sr-only">Facebook</span>
              <Facebook class="h-6 w-6" />
            </a>
            <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
              <span class="sr-only">Instagram</span>
              <Instagram class="h-6 w-6" />
            </a>
            <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
              <span class="sr-only">Twitter</span>
              <Twitter class="h-6 w-6" />
            </a>
            <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
              <span class="sr-only">GitHub</span>
              <Github class="h-6 w-6" />
            </a>
          </div>
          <p class="mt-8 text-center text-base text-gray-400">
            &copy; 2023 Your Company, Inc. All rights reserved.
          </p>
        </div>
      </footer>
    `
  },
    {
      name: 'Simple with social links',
      html: `
        <footer class="bg-white">
          <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 md:flex md:items-center md:justify-between lg:px-8">
            <div class="flex justify-center space-x-6 md:order-2">
              <a href="#" class="text-gray-400 hover:text-gray-500">
                <span class="sr-only">Facebook</span>
                <Facebook class="h-6 w-6" />
              </a>
              <a href="#" class="text-gray-400 hover:text-gray-500">
                <span class="sr-only">Instagram</span>
                <Instagram class="h-6 w-6" />
              </a>
              <a href="#" class="text-gray-400 hover:text-gray-500">
                <span class="sr-only">Twitter</span>
                <Twitter class="h-6 w-6" />
              </a>
              <a href="#" class="text-gray-400 hover:text-gray-500">
                <span class="sr-only">GitHub</span>
                <GitHub class="h-6 w-6" />
              </a>
            </div>
            <div class="mt-8 md:mt-0 md:order-1">
              <p class="text-center text-base text-gray-400">
                &copy; 2023 Your Company, Inc. All rights reserved.
              </p>
            </div>
          </div>
        </footer>
      `
    },
    {
    name: 'Simple with social links dark',
    html: `
      <footer class="bg-white dark:bg-gray-800">
        <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 md:flex md:items-center md:justify-between lg:px-8">
          <div class="flex justify-center space-x-6 md:order-2">
            <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
              <span class="sr-only">Facebook</span>
              <Facebook class="h-6 w-6" />
            </a>
            <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
              <span class="sr-only">Instagram</span>
              <Instagram class="h-6 w-6" />
            </a>
            <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
              <span class="sr-only">Twitter</span>
              <Twitter class="h-6 w-6" />
            </a>
            <a href="#" class="text-gray-400 hover:text-gray-500 dark:hover:text-gray-300">
              <span class="sr-only">GitHub</span>
              <Github class="h-6 w-6" />
            </a>
          </div>
          <div class="mt-8 md:mt-0 md:order-1">
            <p class="text-center text-base text-gray-400">
              &copy; 2023 Your Company, Inc. All rights reserved.
            </p>
          </div>
        </div>
      </footer>
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