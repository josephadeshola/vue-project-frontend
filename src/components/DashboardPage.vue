<template>
  <div>
    <!-- Overlay -->
   
   <SideBar/>
    <div class="p-4 sm:ml-64">
      <div class="p-4 border-2 border-gray-200 border-dashed rounded-lg dark:border-gray-700">
        <div class="grid grid-cols-3 gap-4 mb-4">
          <div class="flex items-center justify-center h-24 rounded bg-gray-50 dark:bg-gray-800">
            <p class="text-2xl text-gray-400 dark:text-gray-500">
              <svg class="w-3.5 h-3.5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 18 18">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 1v16M1 9h16"/>
              </svg>
            </p>
          </div>
          <!-- Other grid items... -->
        </div>
        <div class="flex items-center justify-center h-48 mb-4 rounded bg-gray-50 dark:bg-gray-800">
          <p class="text-2xl text-gray-400 dark:text-gray-500">
            <svg class="w-3.5 h-3.5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 18 18">
              <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 1v16M1 9h16"/>
            </svg>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import SideBar from '../components/SideBar.vue';

// State
const sidebarVisible = ref(false);
const dropdownVisible = ref(false);

// Computed properties
const sidebarClass = computed(() => {
  return sidebarVisible.value 
    ? 'fixed top-0 left-0 z-40 w-64 h-screen transition-transform sm:translate-x-0' 
    : 'fixed top-0 left-0 z-40 w-64 h-screen transition-transform -translate-x-full sm:translate-x-0';
});

const dropdownClass = computed(() => {
  return dropdownVisible.value ? 'py-2 space-y-2' : 'hidden py-2 space-y-2';
});

// Methods
const toggleSidebar = () => {
  sidebarVisible.value = !sidebarVisible.value;
};

const dismissSidebar = () => {
  sidebarVisible.value = false;
};

const toggleDropdown = () => {
  dropdownVisible.value = !dropdownVisible.value;
};
</script>
<style scoped>

</style>
