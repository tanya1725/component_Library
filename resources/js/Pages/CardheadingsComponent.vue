<template>
  <div class="space-y-4">
    <div v-for="(variation, index) in variations" :key="index" class="bg-white rounded-lg shadow-md w-full">
      <div class="p-4 bg-gray-50 border-b">
        <h3 class="text-lg font-semibold text-gray-800">{{ variation.name }}</h3>
      </div>
      <div class="p-4">
        <div class="mb-4">
          <div class="p-4 bg-gray-100 rounded-md">
            <!-- Job Postings Card -->
            <div class="bg-white rounded-lg shadow-sm">
              <div class="p-6">
                <!-- With description -->
                <div v-if="variation.name === 'With description'">
                  <h2 class="text-xl font-semibold text-gray-900">Job Postings</h2>
                  <p class="text-gray-500 mt-1">Lorem ipsum dolor sit amet consectetur adipisicing elit quam corrupti consectetur.</p>
                </div>

                <!-- With description and action -->
                <div class="flex justify-between items-start mb-4" v-else-if="variation.name === 'With description and action'">
                  <div>
                    <h2 class="text-xl font-semibold text-gray-900">Job Postings</h2>
                    <p class="text-gray-500 mt-1">Lorem ipsum dolor sit amet consectetur adipisicing elit quam corrupti consectetur.</p>
                  </div>
                  <button class="px-4 py-2 bg-[#6C5CE7] text-white rounded-md hover:bg-[#5A4BD1] transition-colors">
                    Create new job
                  </button>
                </div>

                <!-- With avatar and actions -->
                <div class="flex justify-between items-center" v-else-if="variation.name === 'With avatar and actions'">
                  <div class="flex items-center">
                    <img 
                      src="https://images.unsplash.com/photo-1519244703995-f4e0f30006d5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" 
                      alt="Tom Cook"
                      class="w-10 h-10 rounded-full mr-4"
                    />
                    <div>
                      <h2 class="text-lg font-semibold text-gray-900">Tom Cook</h2>
                      <p class="text-sm text-gray-500">@tom_cook</p>
                    </div>
                  </div>
                  <div class="flex gap-2">
                    <button class="px-4 py-2 flex items-center gap-2 text-gray-700 bg-white border border-gray-200 rounded-md hover:bg-gray-50">
                      <Phone class="w-4 h-4" />
                      Phone
                    </button>
                    <button class="px-4 py-2 flex items-center gap-2 text-gray-700 bg-white border border-gray-200 rounded-md hover:bg-gray-50">
                      <Mail class="w-4 h-4" />
                      Email
                    </button>
                  </div>
                </div>

                <!-- With avatar, meta, and dropdown -->
                <div v-else-if="variation.name === 'With avatar, meta, and dropdown'" class="space-y-4">
                  <div class="flex justify-between items-start">
                    <div class="flex items-start space-x-4">
                      <img 
                        src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                        alt="Chelsea Hagon"
                        class="w-10 h-10 rounded-full"
                      />
                      <div>
                        <h2 class="text-base font-semibold text-gray-900">Chelsea Hagon</h2>
                        <p class="text-sm text-gray-500">December 9 at 11:43 AM</p>
                      </div>
                    </div>
                    <button class="text-gray-400 hover:text-gray-600">
                      <MoreVertical class="w-5 h-5" />
                    </button>
                  </div>
                  <p class="text-gray-600 text-sm">
                    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Illo impedit sapiente recusandae iusto officiis dolor? Laborum quibusdam quam, quidem vel assumenda repellat inventore sint nesciunt, ullam asperiores magnam placeat eveniet. Aliquam voluptatibus assumenda distinctio veniam quam tempora modi aperiam nemo voluptate reprehenderit quidem, nisi vero est.
                  </p>
                </div>

                <!-- With action -->
                <div class="flex justify-between items-center" v-else-if="variation.name === 'With action'">
                  <h2 class="text-lg font-semibold text-gray-900">Job Postings</h2>
                  <button class="px-4 py-2 bg-[#6C5CE7] text-white rounded-md hover:bg-[#5A4BD1] transition-colors">
                    Create new job
                  </button>
                </div>

                <!-- Simple -->
                <h2 v-else class="text-lg font-semibold text-gray-900">Job Postings</h2>
              </div>
              
              <!-- Job listings for all variations except the avatar meta one -->
              <div v-if="variation.name !== 'With avatar, meta, and dropdown'" class="border-t border-gray-100">
                <div v-for="job in jobs" :key="job.title" 
                  class="flex items-center justify-between p-6 hover:bg-gray-50"
                >
                  <div class="flex items-center space-x-3">
                    <div>
                      <h3 class="text-[#A5B4FC] font-medium">{{ job.title }}</h3>
                      <div class="flex items-center mt-1 text-gray-500">
                        <Users class="w-4 h-4 mr-2" />
                        <span class="text-sm">{{ job.department }}</span>
                      </div>
                    </div>
                  </div>
                  <div class="flex items-center space-x-4">
                    <span class="text-sm text-[#4ADE80]">Full-time</span>
                    <div class="flex items-center text-gray-500">
                      <Globe class="w-4 h-4 mr-2" />
                      <span class="text-sm">Remote</span>
                    </div>
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
import { Users, Globe, Phone, Mail, MoreVertical } from 'lucide-vue-next'

const showCode = ref({})

const jobs = [
  {
    title: 'Back End Developer',
    department: 'Engineering'
  },
  {
    title: 'Front End Developer',
    department: 'Engineering'
  },
  {
    title: 'User Interface Designer',
    department: 'Design'
  }
]

const variations = [
  {
    name: 'Simple',
    html: `
    <div class="bg-white rounded-lg shadow-sm">
      <div class="p-6">
        <h2 class="text-lg font-semibold text-gray-900">Job Postings</h2>
      </div>
      <div class="border-t border-gray-100">
        <!-- Job items here -->
      </div>
    </div>
    `
  },
  {
    name: 'With description',
    html: `
    <div class="bg-white rounded-lg shadow-sm">
      <div class="p-6">
        <h2 class="text-xl font-semibold text-gray-900">Job Postings</h2>
        <p class="text-gray-500 mt-1">Lorem ipsum dolor sit amet consectetur adipisicing elit quam corrupti consectetur.</p>
      </div>
      <div class="border-t border-gray-100">
        <!-- Job items here -->
      </div>
    </div>
    `
  },
  {
    name: 'With action',
    html: `
    <div class="bg-white rounded-lg shadow-sm">
      <div class="p-6 flex justify-between items-center">
        <h2 class="text-lg font-semibold text-gray-900">Job Postings</h2>
        <button class="px-4 py-2 bg-[#6C5CE7] text-white rounded-md hover:bg-[#5A4BD1] transition-colors">
          Create new job
        </button>
      </div>
      <div class="border-t border-gray-100">
        <!-- Job items here -->
      </div>
    </div>
    `
  },
  {
    name: 'With description and action',
    html: `
    <div class="bg-white rounded-lg shadow-sm">
      <div class="p-6">
        <div class="flex justify-between items-start mb-4">
          <div>
            <h2 class="text-xl font-semibold text-gray-900">Job Postings</h2>
            <p class="text-gray-500 mt-1">Lorem ipsum dolor sit amet consectetur adipisicing elit quam corrupti consectetur.</p>
          </div>
          <button class="px-4 py-2 bg-[#6C5CE7] text-white rounded-md hover:bg-[#5A4BD1] transition-colors">
            Create new job
          </button>
        </div>
      </div>
      <div class="border-t border-gray-100">
        <!-- Job items here -->
      </div>
    </div>
    `
  },
  {
    name: 'With avatar and actions',
    html: `
    <div class="bg-white rounded-lg shadow-sm">
      <div class="p-6 flex justify-between items-center">
        <div class="flex items-center">
          <img 
            src="https://images.unsplash.com/photo-1519244703995-f4e0f30006d5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" 
            alt="Tom Cook"
            class="w-10 h-10 rounded-full mr-4"
          />
          <div>
            <h2 class="text-lg font-semibold text-gray-900">Tom Cook</h2>
            <p class="text-sm text-gray-500">@tom_cook</p>
          </div>
        </div>
        <div class="flex gap-2">
          <button class="px-4 py-2 flex items-center gap-2 text-gray-700 bg-white border border-gray-200 rounded-md hover:bg-gray-50">
            <Phone class="w-4 h-4" />
            Phone
          </button>
          <button class="px-4 py-2 flex items-center gap-2 text-gray-700 bg-white border border-gray-200 rounded-md hover:bg-gray-50">
            <Mail class="w-4 h-4" />
            Email
          </button>
        </div>
      </div>
      <div class="border-t border-gray-100">
        <!-- Job items here -->
      </div>
    </div>
    `
  },
  {
    name: 'With avatar, meta, and dropdown',
    html: `
    <div class="bg-white rounded-lg shadow-sm">
      <div class="p-6">
        <div class="space-y-4">
          <div class="flex justify-between items-start">
            <div class="flex items-start space-x-4">
              <img 
                src="https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                alt="Chelsea Hagon"
                class="w-10 h-10 rounded-full"
              />
              <div>
                <h2 class="text-base font-semibold text-gray-900">Chelsea Hagon</h2>
                <p class="text-sm text-gray-500">December 9 at 11:43 AM</p>
              </div>
            </div>
            <button class="text-gray-400 hover:text-gray-600">
              <MoreVertical class="w-5 h-5" />
            </button>
          </div>
          <p class="text-gray-600 text-sm">
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Illo impedit sapiente recusandae iusto officiis dolor? Laborum quibusdam quam, quidem vel assumenda repellat inventore sint nesciunt, ullam asperiores magnam placeat eveniet. Aliquam voluptatibus assumenda distinctio veniam quam tempora modi aperiam nemo voluptate reprehenderit quidem, nisi vero est.
          </p>
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