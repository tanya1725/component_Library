<template>
  <div class="flex h-screen bg-gray-100 font-sans">
    <!-- Sidebar -->
    <aside class="w-64 bg-white shadow-md flex flex-col">
      <div class="p-4">
        <h1 class="text-2xl font-bold text-gray-800">Components Hub</h1>
      </div>
      <nav class="mt-4 flex-1 overflow-y-auto">
        <ul>
          <li v-for="component in filteredComponents" :key="component" class="mb-2">
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
      <!-- Header -->
      <header class="bg-white px-6 py-4 flex justify-between items-center sticky top-0 z-10 shadow">
        <div class="flex items-center space-x-4">
          <input 
            type="text" 
            placeholder="Search components..." 
            class="px-4 py-2 border border-gray-300 rounded focus:outline-none focus:ring-2 focus:ring-blue-500"
            v-model="searchQuery"
          />
        </div>
        <div>
          <button class="mr-4 bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">Login</button>
          <button class="bg-gray-100 text-gray-800 px-4 py-2 rounded hover:bg-gray-200">Register</button>
        </div>
      </header>

      <!-- Content -->
      <div class="container mx-auto px-6 py-8">
        <h2 class="text-3xl font-bold text-gray-800 mb-6">{{ selectedComponent }} Variations</h2>
        <component :is="currentComponent" />
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import ButtonComponent from './ButtonComponent.vue';
import InputComponent from './InputComponent.vue';
import RadioComponent from './RadioComponent.vue';
import HeaderComponent from './HeaderComponent.vue';
import FooterComponent from './FooterComponent.vue';
import FlexibleSidebarComponent from './FlexibleSidebarComponent.vue';
import AboutpageComponent from './AboutpageComponent.vue';
import ActionpanelComponent from './ActionpanelComponent.vue';
import AlertComponent from './AlertComponent.vue';
import AvatarComponent from './AvatarComponent.vue';
import BadgesComponent from './BadgesComponent.vue';
import BannerComponent from './BannerComponent.vue';
import BentogridComponent from './BentogridComponent.vue';
import BlogComponent from './BlogComponent.vue';
import BreadcrumbsComponent from './BreadcrumbsComponent.vue';
import ProgressbarsComponent from './ProgressbarsComponent.vue';
import CalenderComponent from './CalenderComponent.vue';
import CardheadingsComponent from './CardheadingsComponent.vue';

const selectedComponent = ref('Button');
const components = [
  'Button',
  'Input',
  'Radio Groups',
  'Header',
  'Sidebar Layout',
  'Footer',
  'About Page',
  'Action Panel',
  'Alerts',
  'Avatars',
  'Badges',
  'Banners',
  'Bento grids',
  'Blogs',
  'Breadcrumbs',
  'Progress bars',
  'Calender',
  'Card headings'
];

const searchQuery = ref('');
const filteredComponents = computed(() => {
  return components.filter(component =>
    component.toLowerCase().includes(searchQuery.value.toLowerCase())
  );
});

const componentMap = {
  Button: ButtonComponent,
  Input: InputComponent,
  'Radio Groups': RadioComponent,
  Header: HeaderComponent,
  'Sidebar Layout': FlexibleSidebarComponent,
  Footer: FooterComponent,
  'About Page': AboutpageComponent,
  'Action Panel': ActionpanelComponent,
  Alerts: AlertComponent,
  Avatars: AvatarComponent,
  Badges: BadgesComponent,
  Banners: BannerComponent,
  'Bento grids': BentogridComponent,
  Blogs: BlogComponent,
  Breadcrumbs: BreadcrumbsComponent,
  'Progress bars':ProgressbarsComponent,
  Calender:CalenderComponent,
  'Card headings':CardheadingsComponent
};

const currentComponent = computed(() => componentMap[selectedComponent.value]);

const selectComponent = (component) => {
  selectedComponent.value = component;
};
</script>

<style>
/* Style the scrollbar for the sidebar */
aside nav::-webkit-scrollbar {
  width: 8px;
}

aside nav::-webkit-scrollbar-thumb {
  background-color: #cbd5e0;
  border-radius: 4px;
}

aside nav::-webkit-scrollbar-thumb:hover {
  background-color: #a0aec0;
}
</style>
