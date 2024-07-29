<template>
   <div v-if="sidebarVisible" class="fixed inset-0 z-30 bg-black opacity-50" @click="dismissSidebar"></div>
    
    <!-- Sidebar Toggle Button -->
    <div class="bg-white flex justify-between md:justify-end shadow-lg fixed w-full">
    <button @click="toggleSidebar" aria-controls="sidebar-multi-level-sidebar" type="button" class="inline-flex items-center p-2 mt-2 ms-3 text-sm text-gray-500 rounded-lg sm:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600">
      <span class="sr-only">Open sidebar</span>
      <svg class="w-6 h-6" aria-hidden="true" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
        <path clip-rule="evenodd" fill-rule="evenodd" d="M2 4.75A.75.75 0 012.75 4h14.5a.75.75 0 010 1.5H2.75A.75.75 0 012 4.75zm0 10.5a.75.75 0 01.75-.75h7.5a.75.75 0 010 1.5h-7.5a.75.75 0 01-.75-.75zM2 10a.75.75 0 01.75-.75h14.5a.75.75 0 010 1.5H2.75A.75.75 0 012 10z"></path>
      </svg>
    </button>
    <div class="flex justify-end gap-2 md:py-3 px-3">
      <p class="mt-[10px] md:mt-0">Welcome:</p>
      <p class="text-blue-900 md:mt-0 mt-[10px] font-bold">{{userName}}</p>
    </div>
    </div>

    <!-- Sidebar -->
    <aside :class="sidebarClass" id="sidebar-multi-level-sidebar" aria-label="Sidebar">
      <div class="h-full px-3 py-4 overflow-y-auto bg-gray-50 dark:bg-blue-700">
        <ul class="space-y-2 font-medium">
          <li>
            <RouterLink to="/" class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-900  group">
              <i class="bi bi-houses-fill text-white"></i>
              <span class="ms-3">Home</span>
            </RouterLink>
          </li>
          <li>
            <RouterLink to="/dashboard" class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-900  group">
              <i class="bi bi-bag-dash-fill text-white"></i>
              <span class="ms-3">Dashboard</span>
            </RouterLink>
          </li>
          <li>
            <RouterLink to="/job/create" class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-900  group">
             <i class="bi bi-file-post-fill text-white"></i>
              <span class="ms-3">Post Job</span>
            </RouterLink>
          </li>
          <li>
            <a href="#" class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-900  group">
              <svg class="w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 22 21">
                <path d="M16.975 11H10V4.025a1 1 0 0 0-1.066-.998 8.5 8.5 0 1 0 9.039 9.039.999.999 0 0 0-1-1.066h.002Z"/>
                <path d="M12.5 0c-.157 0-.311.01-.565.027A1 1 0 0 0 11 1.02V10h8.975a1 1 0 0 0 1-.935c.013-.188.028-.374.028-.565A8.51 8.51 0 0 0 12.5 0Z"/>
              </svg>
              <span class="ms-3">View posted job</span>
            </a>
          </li>
          <li>
            <a href="#" class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-900  group">
              <svg class="w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 22 21">
                <path d="M16.975 11H10V4.025a1 1 0 0 0-1.066-.998 8.5 8.5 0 1 0 9.039 9.039.999.999 0 0 0-1-1.066h.002Z"/>
                <path d="M12.5 0c-.157 0-.311.01-.565.027A1 1 0 0 0 11 1.02V10h8.975a1 1 0 0 0 1-.935c.013-.188.028-.374.028-.565A8.51 8.51 0 0 0 12.5 0Z"/>
              </svg>
              <span class="ms-3">Setting</span>
            </a>
          </li>
        
          <!-- Other list items... -->
        </ul>
      </div>
    </aside>

</template>

<script>
export default {
  data() {
    return {
      sidebarVisible: false,
      dropdownVisible: false,
      userName: ''
    };
  },
  computed: {
    sidebarClass() {
      return this.sidebarVisible ? 'fixed top-0 left-0 z-40 w-64 h-screen transition-transform sm:translate-x-0' : 'fixed top-0 left-0 z-40 w-64 h-screen transition-transform -translate-x-full sm:translate-x-0';
    },
    dropdownClass() {
      return this.dropdownVisible ? 'py-2 space-y-2' : 'hidden py-2 space-y-2';
    }
  },
  methods: {
    toggleSidebar() {
      this.sidebarVisible = !this.sidebarVisible;
    },
    dismissSidebar() {
      this.sidebarVisible = false;
    },
    toggleDropdown() {
      this.dropdownVisible = !this.dropdownVisible;
    }
  },
  created() {
    this.fetchUserName();
  },
  methods: {
    toggleSidebar() {
      this.sidebarVisible = !this.sidebarVisible;
    },
    dismissSidebar() {
      this.sidebarVisible = false;
    },
    toggleDropdown() {
      this.dropdownVisible = !this.dropdownVisible;
    },
    fetchUserName() {
      const user = JSON.parse(localStorage.getItem('user'));
      console.log(user);
      if (user && user.name) {
        this.userName = user.name;
      } else {
        this.userName = 'Guest';
      }
    }
  }
};
</script>


<style>

</style>