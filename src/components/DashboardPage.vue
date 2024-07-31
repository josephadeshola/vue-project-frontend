<template>
  <div>
    <!-- Overlay -->
   
   <SideBar/>
    <div class="p-4 sm:ml-64">
      <div class="p-4 mt-12">
        <h2>Hellow</h2>
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
