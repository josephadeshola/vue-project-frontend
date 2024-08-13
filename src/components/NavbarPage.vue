<template>
   <nav class="!bg-white border-gray-200 fixed w-full shadow-md z-10">
      <div
        class="flex flex-wrap justify-between items-center mx-auto max-w-screen-xl p-4"
      >
        <RouterLink
          to="/"
          class="flex items-center space-x-3 rtl:space-x-reverse"
        >
          <img
            src="../assets/Advantages.gif"
            class="h-5 md:h-9"
            alt="Flowbite Logo"
          />
          <span
            class="self-center  md:text-xl text-sm font-bold whitespace-nowrap dark:text-black"
            ><span class="text-blue-700">DRC</span>-JobList</span
          >
        </RouterLink>
        <div class="flex items-center space-x-6 rtl:space-x-reverse">
          <RouterLink
            to="/login"
            class="text-sm text-blue-600 dark:text-blue-500 font-semibold hover:underline"
            >Login</RouterLink
          >
          <RouterLink
            to="/register"
            class="text-sm font-semibold hover:underline text-black"
            >Register</RouterLink
          >
          <RouterLink
            to="/dashboard"
            class="text-sm font-semibold hover:underline text-black"
            >Dashboard</RouterLink
          >
        </div>
      </div>
    </nav>
</template>

<script>

</script>

<style>

</style>