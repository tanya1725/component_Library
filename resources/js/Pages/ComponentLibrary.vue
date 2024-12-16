<template>
    <div class="component-library">
      <!-- New Header Component -->
      <header class="site-header">
        <div class="header-left">
          <div class="logo">ComponentHub</div>
          <nav class="main-nav">
            <a href="#" class="nav-link">Home</a>
            <a href="#" class="nav-link">About Us</a>
            <a href="#" class="nav-link">Components</a>
          </nav>
        </div>
        <div class="header-right">
          <button class="btn btn-login">Login</button>
          <button class="btn btn-register">Register</button>
        </div>
      </header>
  
      <div class="main-content">
        <nav class="sidebar">
          <h2>Components</h2>
          <ul>
            <li v-for="component in components" :key="component">
              <button @click="selectComponent(component)" 
                      :class="{ active: selectedComponent === component }">
                {{ component }}
              </button>
            </li>
          </ul>
        </nav>                            
        <main class="content">
          <h1>{{ selectedComponent }} Variations</h1>
          <div class="variations">
            <div v-for="(variation, index) in currentVariations" :key="index" class="variation">
              <h3>{{ variation.name }}</h3>
              <div class="tabs">
                <button @click="activeTab = 'preview'" :class="{ active: activeTab === 'preview' }">Preview</button>
                <button @click="activeTab = 'code'" :class="{ active: activeTab === 'code' }">Code</button>
              </div>
              <div v-if="activeTab === 'preview'" class="preview" v-html="variation.html"></div>
              <pre v-else><code>{{ variation.html }}</code></pre>
            </div>
          </div>
        </main>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        selectedComponent: 'Button',
        components: ['Button', 'Label', 'Input', 'Checkbox'],
        componentVariations: {
          Button: [
    {
      name: 'Basic',
      html: '<button class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600">Basic Button</button>'
    },
    {
      name: 'With Saturation',
      html: `
      <div class="flex-container">
        <button class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600">Default</button>
        <button class="px-4 py-2 bg-gray-500 text-white rounded hover:bg-gray-600">Secondary</button>
        <button class="px-4 py-2 bg-red-500 text-white rounded hover:bg-red-600">Destructive</button>
        <button class="px-4 py-2 border border-gray-300 rounded hover:bg-gray-100">Outline</button>
        <button class="px-4 py-2 text-blue-500 hover:underline">Link</button>
      </div>
    `
    },
    {
      name: 'With Icon',
      html: `
      <div class="flex-container">
        <button class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 flex items-center">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
          Login with Email
        </button>
        <button class="px-4 py-2 bg-gray-500 text-white rounded hover:bg-gray-600 flex items-center">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="5" x2="12" y2="19"></line><line x1="5" y1="12" x2="19" y2="12"></line></svg>
          Add New
        </button>
      </div>
    `
    },
    {
      name: 'With Dropdown',
      html: `
        <div class="relative inline-block text-left">
          <button @click="toggleDropdown" class="px-4 py-2 border border-gray-300 rounded hover:bg-gray-100 flex items-center">
            Options
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 ml-2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="6 9 12 15 18 9"></polyline></svg>
          </button>
          <div v-if="dropdownOpen" class="origin-top-left absolute left-0 mt-2 w-48 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5">
            <div class="py-1" role="menu" aria-orientation="vertical" aria-labelledby="options-menu">
              <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900" role="menuitem">Option 1</a>
              <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900" role="menuitem">Option 2</a>
              <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900" role="menuitem">Option 3</a>
            </div>
          </div>
        </div>
      `
    }
  ],
          Label: [
            { name: 'Default', html: '<label>Default Label</label>' },
            { name: 'Bold', html: '<label class="label-bold">Bold Label</label>' },
            { name: 'Required', html: '<label class="label-required">Required Label</label>' },
          ],
          Input: [
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
    }
  ],
          Checkbox: [
            { name: 'Default', html: '<input type="checkbox" id="defaultCheck"><label for="defaultCheck">Default Checkbox</label>' },
            { name: 'Checked', html: '<input type="checkbox" id="checkedCheck" checked><label for="checkedCheck">Checked Checkbox</label>' },
            { name: 'Disabled', html: '<input type="checkbox" id="disabledCheck" disabled><label for="disabledCheck">Disabled Checkbox</label>' },
          ],
        },
        activeTab: 'preview',
      }
    },
    computed: {
      currentVariations() {
        return this.componentVariations[this.selectedComponent] || []
      }
    },
    methods: {
      selectComponent(component) {
        this.selectedComponent = component
      }
    },
    mounted() {
      this.$nextTick(() => {
        document.querySelectorAll('.btn').forEach(btn => {
          btn.addEventListener('click', () => alert('Button clicked!'))
        })
      })
    }
  }
  </script>
  
  <style scoped>
  /* Header Styles */

/* Header Styles */


.site-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f8f9fa;
  padding: 15px 20px;
  border-bottom: 1px solid #e9ecef;
}

.header-left {
  display: flex;
  align-items: center;
}

.logo {
  font-size: 24px;
  font-weight: bold;
  margin-right: 30px;
  color: #007bff;
}

.main-nav {
  display: flex;
  gap: 20px;
}

.nav-link {
  text-decoration: none;
  color: #495057;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #007bff;
}

.header-right {
  display: flex;
  gap: 15px;
}

.btn-login, .btn-register {
  padding: 8px 15px;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn-login {
  background-color: transparent;
  border: 1px solid #007bff;
  color: #007bff;
}

.btn-register {
  background-color: #007bff;
  color: white;
  border: none;
}

/* Full Height Adjustments */
.component-library {
  display: flex;
  flex-direction: column;
  height: 100vh;
  font-family: Arial, sans-serif;
}

.main-content {
  display: flex;
  flex-grow: 1;
  overflow: hidden;
}

.sidebar {
  width: 300px;
  background-color: #f0f0f0;
  padding: 20px;
  border-right: 1px solid #ccc;
  overflow-y: auto;
}

.content {
  flex-grow: 1;
  padding: 20px;
  overflow-y: auto;
}

.sidebar h2 {
  margin-top: 0;
}

.sidebar ul {
  list-style-type: none;
  padding: 0;
}

.sidebar button {
  width: 100%;
  text-align: left;
  padding: 10px;
  margin-bottom: 5px;
  background: none;
  border: none;
  cursor: pointer;
}

.sidebar button.active {
  background-color: #ddd;
  font-weight: bold;
}

.variations {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}

.variation {
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 15px;
}

.preview {
  margin-bottom: 10px;
  padding: 10px;
  background-color: #f9f9f9;
  border-radius: 4px;
}

pre {
  background-color: #f0f0f0;
  padding: 10px;
  border-radius: 4px;
  overflow-x: auto;
}
  
  /* Custom component styles */
  .btn {
    padding: 10px 15px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .btn-primary {
    background-color: #007bff;
    color: white;
  }
  
  .btn-secondary {
    background-color: #6c757d;
    color: white;
  }
  
  .label-bold {
    font-weight: bold;
  }
  
  .label-required::after {
    content: " *";
    color: red;
  }
  
  input[type="text"],
  input[type="password"],
  input[type="number"] {
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  input[type="checkbox"] {
    margin-right: 5px;
  }
  
  .tabs {
    display: flex;
    margin-bottom: 70px;
  }
  
  .tabs button {
    padding: 5px 10px;
    border: 1px solid #ccc;
    background-color: #f0f0f0;
    cursor: pointer;
  }
  
  .tabs button.active {
    background-color: #fff;
    border-bottom-color: #fff;
  }
  
  .tabs button:first-child {
    border-top-left-radius: 4px;
    border-bottom-left-radius: 4px;
  }
  
  .tabs button:last-child {
    border-top-right-radius: 4px;
    border-bottom-right-radius: 4px;
  }
  </style>