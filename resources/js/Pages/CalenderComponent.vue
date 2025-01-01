<template>
  <div class="space-y-8 p-8">
    <div v-for="(variation, index) in variations" :key="index" class="bg-white rounded-lg shadow-md w-full">
      <div class="p-4 bg-gray-50 border-b">
        <h3 class="text-lg font-semibold text-gray-800">{{ variation.name }}</h3>
      </div>
      <div class="p-4">
        <div class="mb-4">
          <div class="p-4 bg-gray-50 rounded-md">
            <component :is="variation.component" />
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
            <code class="text-sm text-white">{{ variation.code }}</code>
          </pre>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted,computed } from 'vue'
import { Calendar, ChevronLeft, ChevronRight, MapPin, MoreHorizontal, ChevronDown } from 'lucide-vue-next'

const showCode = ref({})
const showViewDropdown = ref(false)

const meetings = [
  {
    name: 'Leslie Alexander',
    time: 'January 10th, 2022 at 5:00 PM',
    location: 'Starbucks',
    avatar: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80'
  },
  {
    name: 'Michael Foster',
    time: 'January 12th, 2022 at 3:00 PM',
    location: 'Tim Hortons',
    avatar: 'https://images.unsplash.com/photo-1519244703995-f4e0f30006d5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80'
  },
  {
    name: 'Dries Vincent',
    time: 'January 12th, 2022 at 5:00 PM',
    location: 'Costa Coffee at Braehead',
    avatar: 'https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80'
  },
  {
    name: 'Lindsay Walton',
    time: 'January 14th, 2022 at 10:00 AM',
    location: 'Silverburn',
    avatar: 'https://images.unsplash.com/photo-1517841905240-472988babdf9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80'
  },
  {
    name: 'Courtney Henry',
    time: 'January 14th, 2022 at 12:00 PM',
    location: 'The Glasgow Green',
    avatar: 'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80'
  }
]

const SmallWithMeetings = {
  setup() {
    const dates = ref([
      ...Array.from({ length: 31 }, (_, i) => ({
        day: i + 1,
        isPrevMonth: i < 3,
        isNextMonth: i > 30
      }))
    ])

    return { 
      meetings, 
      dates,
      ChevronLeft, 
      ChevronRight, 
      Calendar, 
      MapPin, 
      MoreHorizontal 
    }
  },
  template: `
   <div class="bg-white rounded-lg p-6 border border-gray-200">
  <h2 class="text-xl font-semibold text-gray-900 mb-6">Upcoming meetings</h2>
  
  <div class="flex flex-row-reverse">
    <!-- Calendar Section -->
    <div class="w-80 ml-4 border rounded-lg p-4 border-gray-200">
      <div class="flex items-center justify-between mb-4">
        <button class="p-1 hover:bg-gray-100 rounded-full">
          <ChevronLeft class="h-5 w-5 text-gray-500" />
        </button>
        <h3 class="text-base font-semibold text-gray-900">January</h3>
        <button class="p-1 hover:bg-gray-100 rounded-full">
          <ChevronRight class="h-5 w-5 text-gray-500" />
        </button>
      </div>
      
      <div class="grid grid-cols-7 text-center text-xs leading-6 text-gray-500 mb-1">
        <div>M</div>
        <div>T</div>
        <div>W</div>
        <div>T</div>
        <div>F</div>
        <div>S</div>
        <div>S</div>
      </div>
      
      <div class="grid grid-cols-7 text-sm">
        <div v-for="(date, i) in dates" :key="i"
          class="py-1.5 flex items-center justify-center"
        >
          <button
            :class="[
              'w-8 h-8 flex items-center justify-center rounded-full',
              date.day === 22 && !date.isPrevMonth && !date.isNextMonth ? 'bg-gray-900 text-white font-semibold' : '',
              date.day === 12 && !date.isPrevMonth && !date.isNextMonth ? 'text-indigo-600 font-semibold' : '',
              (date.isPrevMonth || date.isNextMonth) ? 'text-gray-400' : 'text-gray-900',
            ]"
          >
            {{ date.day }}
          </button>
        </div>
      </div>
    </div>

    <!-- Meetings List Section -->
    <div class="flex-1 space-y-6">
      <div v-for="meeting in meetings" :key="meeting.name" 
        class="flex items-start group relative"
      >
        <img :src="meeting.avatar" :alt="meeting.name" class="w-10 h-10 rounded-full mr-4 flex-shrink-0">
        <div class="flex-1 min-w-0">
          <h4 class="text-sm font-medium text-gray-900">{{ meeting.name }}</h4>
          <div class="flex items-center text-sm text-gray-500 mt-1 space-x-3">
            <div class="flex items-center">
              <svg class="w-4 h-4 mr-1.5 flex-shrink-0 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
              </svg>
              <span>{{ meeting.time }}</span>
            </div>
            <div class="h-4 w-px bg-gray-200"></div>
            <div class="flex items-center">
              <svg class="w-4 h-4 mr-1.5 flex-shrink-0 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
              </svg>
              <span>{{ meeting.location }}</span>
            </div>
          </div>
        
        </div>
        <button class="opacity-0 group-hover:opacity-100 transition-opacity duration-150 ease-in-out absolute right-0 top-0 p-2 text-gray-400 hover:text-gray-500 rounded-full hover:bg-gray-100">
          <MoreHorizontal class="w-5 h-5" />
        </button>
      </div>
    </div>
  </div>

  <div class="mt-6">
        <button class="w-full px-4 py-2 text-sm font-medium text-white bg-indigo-600 rounded-md hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
          Add event
        </button>
  </div>
</div>
  `
}

const MonthView = {
  setup() {
    return { ChevronLeft, ChevronRight }
  },
  template: `
    <div class="bg-white rounded-lg shadow overflow-hidden min-h-[600px]">
      <div class="flex items-center justify-between p-4 border-b">
        <h2 class="text-xl font-semibold">January 2022</h2>
        <div class="flex items-center space-x-4">
          <button class="px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50">
            Today
          </button>
          <div class="flex">
            <button class="p-2 hover:bg-gray-100 rounded-l-md">
              <ChevronLeft class="w-5 h-5" />
            </button>
            <button class="p-2 hover:bg-gray-100 rounded-r-md">
              <ChevronRight class="w-5 h-5" />
            </button>
          </div>
          <select class="px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md">
            <option>Month view</option>
          </select>
          <button class="px-4 py-2 text-sm font-medium text-white bg-indigo-600 rounded-md hover:bg-indigo-700">
            Add event
          </button>
        </div>
      </div>
      <div class="grid grid-cols-7 border-b">
        <div v-for="day in ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']" :key="day"
          class="px-2 py-3 text-sm font-medium text-gray-900 border-r last:border-r-0"
        >
          {{ day }}
        </div>
      </div>
      <div class="grid grid-cols-7 grid-rows-5 h-full">
        <div v-for="date in 35" :key="date" 
          class="min-h-[100px] p-2 border-b border-r last:border-r-0 relative"
          :class="{'bg-gray-50': date < 4}"
        >
          <span :class="[
            'text-sm',
            date < 4 ? 'text-gray-400' : 'text-gray-900'
          ]">{{ date < 4 ? 31 - (3 - date) : date - 3 }}</span>
          <div v-if="date === 7" class="mt-1">
            <div class="bg-gray-100 p-1 text-xs rounded">
              <div>Design review</div>
              <div class="text-gray-500">10AM</div>
            </div>
            <div class="bg-gray-100 p-1 text-xs rounded mt-1">
              <div>Sales meeting</div>
              <div class="text-gray-500">2PM</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  `
}

const WeekView = {
  setup() {
    return { ChevronLeft, ChevronRight }
  },
  template: `
    <div class="bg-white rounded-lg shadow overflow-hidden min-h-[600px]">
      <div class="flex items-center justify-between p-4 border-b">
        <h2 class="text-xl font-semibold">January 2022</h2>
        <div class="flex items-center space-x-4">
          <button class="px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50">
            Today
          </button>
          <div class="flex">
            <button class="p-2 hover:bg-gray-100 rounded-l-md">
              <ChevronLeft class="w-5 h-5" />
            </button>
            <button class="p-2 hover:bg-gray-100 rounded-r-md">
              <ChevronRight class="w-5 h-5" />
            </button>
          </div>
          <select class="px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md">
            <option>Week view</option>
          </select>
          <button class="px-4 py-2 text-sm font-medium text-white bg-indigo-600 rounded-md hover:bg-indigo-700">
            Add event
          </button>
        </div>
      </div>
      <div class="grid grid-cols-8 h-full">
        <div class="border-r pt-16">
          <div v-for="hour in Array.from({ length: 12 }, (_, i) => i + 6)" :key="hour" 
            class="h-20 border-t text-right pr-2 text-sm text-gray-500"
          >
            {{ hour }}:00 AM
          </div>
        </div>
        <div v-for="day in ['Mon 10', 'Tue 11', 'Wed 12', 'Thu 13', 'Fri 14', 'Sat 15', 'Sun 16']" :key="day"
          class="border-r last:border-r-0"
        >
          <div class="text-sm font-medium p-2 text-center border-b">{{ day }}</div>
          <div class="relative h-full">
            <div v-if="day === 'Wed 12'" class="absolute top-24 left-0 right-0 mx-2">
              <div class="bg-blue-100 text-blue-700 p-2 text-xs rounded">
                <div>Breakfast</div>
                <div>6:00 AM</div>
              </div>
              <div class="bg-pink-100 text-pink-700 p-2 text-xs rounded mt-2">
                <div>Flight to Paris</div>
                <div>7:30 AM</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  `
}

const DayView = {
  setup() {
    const showViewDropdown = ref(false)

const toggleViewDropdown = () => {
  showViewDropdown.value = !showViewDropdown.value
}

const formatHour = (hour) => {
  const h = hour % 12 || 12
  const ampm = hour < 12 ? 'AM' : 'PM'
  return `${h.toString().padStart(2, '0')}${ampm}`
}

const schedulerScroll = ref(null)

onMounted(() => {
  if (schedulerScroll.value) {
    // Set scroll to 11 AM (11 * 60 = 660 minutes)
    schedulerScroll.value.scrollTop = 660
  }
})

    return { ChevronLeft, ChevronRight, ChevronDown, toggleViewDropdown, formatHour }
  },
  template: `
  <div class="bg-white min-h-[600px] flex flex-col">
    <!-- Header -->
    <div class="p-6">
      <div class="flex items-center justify-between">
        <div>
          <h2 class="text-2xl font-semibold text-gray-900">January 22, 2022</h2>
          <p class="text-sm text-gray-500 mt-1">Saturday</p>
        </div>
        <div class="flex items-center space-x-3">
          <div class="flex items-center rounded-lg border border-gray-200">
            <button class="p-2 hover:bg-gray-50">
              <ChevronLeft class="w-4 h-4 text-gray-600" />
            </button>
            <button class="px-3 py-1.5 text-sm font-medium text-gray-700 hover:bg-gray-50 border-x border-gray-200">
              Today
            </button>
            <button class="p-2 hover:bg-gray-50">
              <ChevronRight class="w-4 h-4 text-gray-600" />
            </button>
          </div>
          
          <div class="relative">
            <button 
              @click="toggleViewDropdown"
              class="flex items-center px-3 py-1.5 text-sm font-medium text-gray-700 bg-white border border-gray-200 rounded-lg hover:bg-gray-50"
            >
              Day view
              <ChevronDown class="ml-2 h-4 w-4" />
            </button>
            
            <div v-if="showViewDropdown" 
              class="absolute right-0 mt-1 w-36 rounded-lg shadow-lg bg-white border border-gray-200 py-1"
            >
              <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-50">Month view</a>
              <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-50">Week view</a>
              <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-50">Day view</a>
            </div>
          </div>

          <button class="px-4 py-1.5 text-sm font-medium text-white bg-[#6C5CE7] rounded-lg hover:bg-[#5A4BD1]">
            Add event
          </button>
        </div>
      </div>
    </div>

    <div class="flex flex-1 overflow-hidden">
      <!-- Time Column -->
      <div class="w-24 border-r border-gray-200 bg-white">
        <div class="relative">
          <div v-for="hour in 24" :key="hour" class="sticky left-0">
            <div class="h-[60px] border-t border-gray-200 text-right pr-3">
              <span class="text-xs text-gray-500 relative -top-2">
                {{ formatHour(hour - 1) }}
              </span>
            </div>
          </div>
        </div>
      </div>

      <!-- Events Column -->
      <div class="flex-1 overflow-y-auto scheduler-scroll"
           style="scrollbar-width: thin; scrollbar-color: #E2E8F0 transparent; height: 600px;"
           ref="schedulerScroll">
        <div class="relative" style="height: 1440px">
          <!-- Breakfast Event -->
          <div class="absolute left-4 right-4 top-[360px]">
            <div class="bg-blue-50 p-3 rounded-lg">
              <div class="text-blue-600 font-medium text-sm">6:00 AM</div>
              <div class="text-blue-700 font-medium">Breakfast</div>
            </div>
          </div>

          <!-- Flight Event -->
          <div class="absolute left-4 right-4 top-[450px]">
            <div class="bg-pink-50 p-3 rounded-lg">
              <div class="text-pink-600 font-medium text-sm">7:30 AM</div>
              <div class="text-pink-700 font-medium">Flight to Paris</div>
              <div class="text-pink-600/90 text-sm mt-1">John F. Kennedy International Airport</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Mini Calendar -->
      <div class="w-[400px] border-l border-gray-200 p-6">
        <div class="text-center">
          <div class="flex items-center justify-between mb-6">
            <button class="p-1.5 hover:bg-gray-50 rounded-lg">
              <ChevronLeft class="w-5 h-5 text-gray-600" />
            </button>
            <h3 class="text-base font-medium">January 2022</h3>
            <button class="p-1.5 hover:bg-gray-50 rounded-lg">
              <ChevronRight class="w-5 h-5 text-gray-600" />
            </button>
          </div>
          
          <div class="grid grid-cols-7 mb-2">
            <div v-for="day in ['M', 'T', 'W', 'T', 'F', 'S', 'S']" :key="day" 
              class="p-2 text-sm font-medium text-gray-500">
              {{ day }}
            </div>
          </div>
          
          <div class="rounded-2xl bg-white shadow-sm border border-gray-200 overflow-hidden">
            <div class="grid grid-cols-7 text-sm divide-x divide-gray-200">
              <template v-for="i in 42" :key="i">
                <div 
                  class="p-4 flex items-center justify-center border-b border-gray-200"
                  :class="{
                    'text-gray-400': i <= 3 || i >= 32,
                    'bg-gray-900 text-white': i === 22,
                    'text-[#6C5CE7]': i === 20,
                  }"
                >
                  {{ i <= 3 ? 27 + i : i >= 32 ? i - 31 : i - 3 }}
                </div>
              </template>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  `
}

const YearView = {
  setup() {
    const months = ref([
      { name: 'January', dates: generateDates(2022, 0) },
      { name: 'February', dates: generateDates(2022, 1) },
      { name: 'March', dates: generateDates(2022, 2) },
      { name: 'April', dates: generateDates(2022, 3) },
      { name: 'May', dates: generateDates(2022, 4) },
      { name: 'June', dates: generateDates(2022, 5) },
      { name: 'July', dates: generateDates(2022, 6) },
      { name: 'August', dates: generateDates(2022, 7) },
      { name: 'September', dates: generateDates(2022, 8) },
      { name: 'October', dates: generateDates(2022, 9) },
      { name: 'November', dates: generateDates(2022, 10) },
      { name: 'December', dates: generateDates(2022, 11) },
    ])

    function generateDates(year, month) {
      const firstDay = new Date(year, month, 1)
      const lastDay = new Date(year, month + 1, 0)
      const daysInMonth = lastDay.getDate()
      const startingDayOfWeek = firstDay.getDay() || 7 // Convert Sunday (0) to 7
      
      const dates = []
      
      // Add days from previous month
      const daysFromPrevMonth = startingDayOfWeek - 1
      const prevMonth = new Date(year, month - 1, 0)
      const prevMonthDays = prevMonth.getDate()
      
      for (let i = daysFromPrevMonth - 1; i >= 0; i--) {
        dates.push({
          value: prevMonthDays - i,
          isCurrentMonth: false,
          isToday: false,
          isSelected: false
        })
      }
      
      // Add days from current month
      const today = new Date()
      const isCurrentYearAndMonth = today.getFullYear() === year && today.getMonth() === month
      
      for (let i = 1; i <= daysInMonth; i++) {
        dates.push({
          value: i,
          isCurrentMonth: true,
          isToday: isCurrentYearAndMonth && today.getDate() === i,
          isSelected: month === 0 && i === 12 // January 12th selected as example
        })
      }
      
      // Add days from next month
      const totalDays = 42 // 6 rows × 7 days
      const remainingDays = totalDays - dates.length
      
      for (let i = 1; i <= remainingDays; i++) {
        dates.push({
          value: i,
          isCurrentMonth: false,
          isToday: false,
          isSelected: false
        })
      }
      
      return dates
    }

    return { months, ChevronLeft, ChevronRight }
  },
  template: `
    <div class="bg-white rounded-lg shadow overflow-hidden">
      <div class="flex items-center justify-between p-4 border-b sticky top-0 bg-white z-10">
        <h2 class="text-xl font-semibold">2022</h2>
        <div class="flex items-center space-x-4">
          <button class="px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md hover:bg-gray-50">
            Today
          </button>
          <div class="flex">
            <button class="p-2 hover:bg-gray-100 rounded-l-md">
              <ChevronLeft class="w-5 h-5" />
            </button>
            <button class="p-2 hover:bg-gray-100 rounded-r-md">
              <ChevronRight class="w-5 h-5" />
            </button>
          </div>
          <select class="px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md">
            <option>Year view</option>
          </select>
          <button class="px-4 py-2 text-sm font-medium text-white bg-[#6C5CE7] rounded-md hover:bg-[#5A4BD1]">
            Add event
          </button>
        </div>
      </div>
      <div class="grid grid-cols-3 gap-6 p-6 max-h-[calc(100vh-80px)] overflow-y-auto"
       style="scrollbar-width: thin; scrollbar-color: #E2E8F0 transparent; --scrollbar-width: 6px; --scrollbar-track: transparent; --scrollbar-thumb: #E2E8F0;"
       :style="{
         '--webkit-scrollbar': 'width: 6px',
         '--webkit-scrollbar-track': 'background: transparent',
         '--webkit-scrollbar-thumb': 'background-color: #E2E8F0; border-radius: 3px'
       }">
        <div v-for="month in months" :key="month.name" class="space-y-2">
          <h3 class="font-medium">{{ month.name }}</h3>
          <div class="border rounded-lg overflow-hidden">
            <div class="grid grid-cols-7 text-center text-xs divide-x divide-gray-200 bg-gray-50">
              <div v-for="day in ['M', 'T', 'W', 'T', 'F', 'S', 'S']" :key="day" 
                class="text-gray-500 py-2 border-b">
                {{ day }}
              </div>
            </div>
            <div class="grid grid-cols-7 text-center text-sm divide-x divide-gray-200">
              <div v-for="date in month.dates" :key="date.value" 
                :class="[
                  'py-2 border-b last:border-b-0',
                  date.isCurrentMonth ? 'text-gray-900' : 'text-gray-400',
                  date.isToday ? 'bg-[#6C5CE7] text-white font-semibold' : '',
                  date.isSelected ? 'text-[#6C5CE7] font-semibold' : ''
                ]"
              >
                {{ date.value }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  `
}

const DoubleView = {
  setup() {
    function generateDates(year, month) {
  const firstDay = new Date(year, month, 1)
  const lastDay = new Date(year, month + 1, 0)
  const daysInMonth = lastDay.getDate()
  const startingDayOfWeek = firstDay.getDay() || 7 // Convert Sunday (0) to 7

  const dates = []

  // Add days from previous month
  const daysFromPrevMonth = startingDayOfWeek - 1
  const prevMonth = new Date(year, month - 1, 0)
  const prevMonthDays = prevMonth.getDate()

  for (let i = daysFromPrevMonth - 1; i >= 0; i--) {
    dates.push({
      value: prevMonthDays - i,
      isCurrentMonth: false,
      isSelected: false
    })
  }

  // Add days from current month
  for (let i = 1; i <= daysInMonth; i++) {
    dates.push({
      value: i,
      isCurrentMonth: true,
      isSelected: month === 0 && i === 12 // January 12th selected
    })
  }

  // Add days from next month
  const totalDays = 42 // 6 rows × 7 days
  const remainingDays = totalDays - dates.length

  for (let i = 1; i <= remainingDays; i++) {
    dates.push({
      value: i,
      isCurrentMonth: false,
      isSelected: false
    })
  }

  return dates
}

const januaryDates = ref(generateDates(2024, 0))
const februaryDates = ref(generateDates(2024, 1))
    return { ChevronLeft, ChevronRight ,januaryDates,februaryDates}
  },
  template: `
 <div class="bg-white rounded-lg shadow-sm overflow-hidden max-w-4xl mx-auto">
    <div class="grid grid-cols-2 divide-x divide-gray-100">
      <!-- January -->
      <div class="p-6">
        <div class="flex items-center justify-between mb-6">
          <button class="p-2 hover:bg-gray-50 rounded-full">
            <ChevronLeft class="h-5 w-5 text-gray-400" />
          </button>
          <h2 class="text-base font-semibold text-gray-900">January</h2>
          <button class="p-2 hover:bg-gray-50 rounded-full">
            <ChevronRight class="h-5 w-5 text-gray-400" />
          </button>
        </div>
        <div class="grid grid-cols-7 text-center mb-2">
          <div v-for="day in ['M', 'T', 'W', 'T', 'F', 'S', 'S']" :key="day" 
            class="text-xs font-medium text-gray-500 mb-1">
            {{ day }}
          </div>
        </div>
        <div class="grid grid-cols-7 gap-0 text-sm border border-gray-100 rounded-lg overflow-hidden">
          <div v-for="date in januaryDates" :key="date.value" 
            :class="[
              'h-10 flex items-center justify-center border border-gray-100',
              date.isCurrentMonth ? 'text-gray-900' : 'text-gray-400',
              date.isSelected ? 'bg-[#6C5CE7] text-white font-medium' : ''
            ]"
          >
            {{ date.value }}
          </div>
        </div>
      </div>

      <!-- February -->
      <div class="p-6">
        <div class="flex items-center justify-between mb-6">
          <button class="p-2 hover:bg-gray-50 rounded-full">
            <ChevronLeft class="h-5 w-5 text-gray-400" />
          </button>
          <h2 class="text-base font-semibold text-gray-900">February</h2>
          <button class="p-2 hover:bg-gray-50 rounded-full">
            <ChevronRight class="h-5 w-5 text-gray-400" />
          </button>
        </div>
        <div class="grid grid-cols-7 text-center mb-2">
          <div v-for="day in ['M', 'T', 'W', 'T', 'F', 'S', 'S']" :key="day" 
            class="text-xs font-medium text-gray-500 mb-1">
            {{ day }}
          </div>
        </div>
        <div class="grid grid-cols-7 gap-0 text-sm border border-gray-100 rounded-lg overflow-hidden">
          <div v-for="date in februaryDates" :key="date.value" 
            :class="[
              'h-10 flex items-center justify-center border border-gray-100',
              date.isCurrentMonth ? 'text-gray-900' : 'text-gray-400'
            ]"
          >
            {{ date.value }}
          </div>
        </div>
      </div>
    </div>

    <!-- Upcoming Events Section -->
    <div class="border-t border-gray-100 p-6">
      <h3 class="text-base font-semibold text-gray-900 mb-4">Upcoming events</h3>
      <div class="space-y-6">
        <div class="flex items-start justify-between">
          <div>
            <p class="text-sm text-gray-500">Wed, Jan 12</p>
            <p class="text-sm text-gray-500 mt-1">Nothing on today's schedule</p>
          </div>
        </div>

        <div class="flex items-start justify-between">
          <div>
            <p class="text-sm text-gray-500">Thu, Jan 13</p>
            <p class="text-sm text-gray-900 mt-1">View house with real estate agent</p>
          </div>
          <p class="text-sm text-gray-500">2:30 PM - 4:30 PM</p>
        </div>

        <div class="flex items-start justify-between">
          <div>
            <p class="text-sm text-gray-500">Fri, Jan 14</p>
            <p class="text-sm text-gray-900 mt-1">Meeting with bank manager</p>
          </div>
          <p class="text-sm text-gray-500">All day</p>
        </div>

        <div class="flex items-start justify-between">
          <div>
            <p class="text-sm text-gray-500">Mon, Jan 17</p>
            <p class="text-sm text-gray-900 mt-1">Sign paperwork at lawyers</p>
          </div>
          <p class="text-sm text-gray-500">10:00 AM - 10:15 AM</p>
        </div>
      </div>
    </div>
  </div>
  `
}

const BorderlessStacked = {
  setup() {
    const meetings = [
  {
    name: 'Leslie Alexander',
    time: '1:00 PM - 2:30 PM',
    avatar: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80'
  },
  {
    name: 'Michael Foster',
    time: '3:00 PM - 4:30 PM',
    avatar: 'https://images.unsplash.com/photo-1519244703995-f4e0f30006d5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80'
  },
  {
    name: 'Dries Vincent',
    time: '5:00 PM - 6:30 PM',
    avatar: 'https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80'
  }
]

const dates = ref(generateDates(2022, 0)) // January 2022

const weeks = computed(() => {
  const weekArray = []
  for (let i = 0; i < dates.value.length; i += 7) {
    weekArray.push(dates.value.slice(i, i + 7))
  }
  return weekArray
})

function generateDates(year, month) {
  const firstDay = new Date(year, month, 1)
  const lastDay = new Date(year, month + 1, 0)
  const daysInMonth = lastDay.getDate()
  const startingDayOfWeek = firstDay.getDay() || 7 // Convert Sunday (0) to 7

  const dates = []

  // Add days from previous month
  const daysFromPrevMonth = startingDayOfWeek - 1
  const prevMonth = new Date(year, month - 1, 0)
  const prevMonthDays = prevMonth.getDate()

  for (let i = daysFromPrevMonth - 1; i >= 0; i--) {
    dates.push({
      value: prevMonthDays - i,
      isCurrentMonth: false,
      isSelected: false,
      isHighlighted: false
    })
  }

  // Add days from current month
  for (let i = 1; i <= daysInMonth; i++) {
    dates.push({
      value: i,
      isCurrentMonth: true,
      isSelected: i === 21, // January 21st selected
      isHighlighted: i === 12 // January 12th highlighted
    })
  }

  // Add days from next month
  const totalDays = 42 // 6 rows × 7 days
  const remainingDays = totalDays - dates.length

  for (let i = 1; i <= remainingDays; i++) {
    dates.push({
      value: i,
      isCurrentMonth: false,
      isSelected: false,
      isHighlighted: false
    })
  }

  return dates
}
    return { meetings, ChevronLeft, ChevronRight,weeks }
  },
  template: `
    <div class="bg-white rounded-lg max-w-md mx-auto">
    <div class="p-8">
      <!-- Calendar Header -->
      <div class="text-center mb-8">
        <div class="flex items-center justify-center gap-8">
          <button class="p-2 hover:bg-gray-50 rounded-full">
            <ChevronLeft class="h-5 w-5 text-gray-400" />
          </button>
          <h2 class="text-lg font-medium">January 2022</h2>
          <button class="p-2 hover:bg-gray-50 rounded-full">
            <ChevronRight class="h-5 w-5 text-gray-400" />
          </button>
        </div>
      </div>

      <!-- Calendar Grid -->
      <div class="mb-8">
        <!-- Days Header -->
        <div class="grid grid-cols-7 text-center mb-2">
          <div v-for="day in ['M', 'T', 'W', 'T', 'F', 'S', 'S']" :key="day" 
            class="text-sm text-gray-600">
            {{ day }}
          </div>
        </div>

        <!-- Calendar Dates -->
        <div class="grid grid-cols-7 text-sm divide-y divide-gray-200 -mx-1">
          <template v-for="(week, weekIndex) in weeks" :key="weekIndex">
            <div v-for="date in week" :key="date.value" 
              :class="[
                'py-2 flex items-center justify-center',
                date.isCurrentMonth ? 'text-gray-900' : 'text-gray-400',
                date.isSelected ? 'bg-gray-900 text-white rounded-full w-8 h-8 flex items-center justify-center' : '',
                date.isHighlighted ? 'text-[#6C5CE7] font-medium' : '',
                weekIndex === 0 ? 'border-t border-gray-200' : ''
              ]"
            >
              {{ date.value }}
            </div>
          </template>
        </div>
      </div>

      <!-- Schedule Section -->
      <div class="space-y-6">
        <h3 class="text-lg font-medium">Schedule for January 21, 2022</h3>
        <div class="space-y-6">
          <div v-for="meeting in meetings" :key="meeting.name" class="flex items-center gap-4">
            <img 
              :src="meeting.avatar" 
              :alt="meeting.name"
              class="w-10 h-10 rounded-full"
            >
            <div>
              <div class="font-medium">{{ meeting.name }}</div>
              <div class="text-sm text-gray-500">{{ meeting.time }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  `
}

const BorderlessSideBySide = {
  setup() {
    return { meetings, ChevronLeft, ChevronRight }
  },
  template: `
    <div class="bg-white rounded-lg shadow overflow-hidden">
      <div class="grid grid-cols-2">
        <div class="p-4">
          <div class="text-center mb-8">
            <h2 class="text-lg font-semibold mb-4">January 2022</h2>
            <div class="inline-flex">
              <button class="p-1"><ChevronLeft class="h-5 w-5 text-gray-500" /></button>
              <button class="p-1"><ChevronRight class="h-5 w-5 text-gray-500" /></button>
            </div>
          </div>
          <div class="grid grid-cols-7 text-center mb-2">
            <div v-for="day in ['M', 'T', 'W', 'T', 'F', 'S', 'S']" :key="day" class="text-xs font-medium text-gray-500">
              {{ day }}
            </div>
          </div>
          <div class="grid grid-cols-7 gap-1 text-sm">
            <div v-for="date in 31" :key="date" 
              :class="[
                'h-8 flex items-center justify-center rounded-full',
                date === 21 ? 'bg-black text-white' : '',
                date === 12 ? 'text-indigo-600 font-semibold' : ''
              ]"
            >
              {{ date }}
            </div>
          </div>
        </div>
        <div class="p-4 border-l">
          <h3 class="text-lg font-semibold mb-4">Schedule for January 21, 2022</h3>
          <div class="space-y-4">
            <div v-for="meeting in meetings" :key="meeting.name" class="flex items-center">
              <img :src="meeting.avatar" class="w-10 h-10 rounded-full mr-4" :alt="meeting.name">
              <div>
                <h4 class="text-sm font-medium">{{ meeting.name }}</h4>
                <p class="text-sm text-gray-500">{{ meeting.time }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  `
}

const variations = [
  { name: 'Small with meetings', component: SmallWithMeetings, code: SmallWithMeetings.template },
  { name: 'Month view', component: MonthView, code: MonthView.template },
  { name: 'Week view', component: WeekView, code: WeekView.template },
  { name: 'Day view', component: DayView, code: DayView.template },
  { name: 'Year view', component: YearView, code: YearView.template },
  { name: 'Double', component: DoubleView, code: DoubleView.template },
  { name: 'Borderless stacked', component: BorderlessStacked, code: BorderlessStacked.template },
  { name: 'Borderless side-by-side', component: BorderlessSideBySide, code: BorderlessSideBySide.template },
]

const toggleCode = (index) => {
  showCode.value[index] = !showCode.value[index]
}
</script>

<style scoped>
/* Add any additional styles here if needed */
</style>