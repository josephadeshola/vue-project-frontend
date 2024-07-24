<template>
  <div class="bg-slate-200 h-screen flex items-center justify-center py-5">
    <div class="max-w-md w-full p-4 shadow-lg bg-white rounded">
      <p class="text-center font-bold text-3xl">Login</p>
      <div class="py-3 px-5">
        <hr class="text-blue-500">
      </div>
      <form class="space-y-4">
        <!-- Email -->
        <div>
          <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
          <input
            id="email"
            name="email"
            type="email"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
            placeholder="Enter your email address"
          />
        </div>

        <!-- Password -->
        <div>
          <label for="password" class="block text-sm -mt-1 font-medium text-gray-700">Password</label>
          <input
            id="password"
            name="password"
            type="password"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
            placeholder="Enter your password"
          />
        </div>

        <!-- Submit Button -->
        <div>
          <button
            type="submit"
            class="w-full px-4 py-2 bg-blue-600 text-white font-medium rounded-md shadow-sm hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500"
          >
            Login
          </button>
          <p class="text-sm mt-2 text-center">Don't have an account?  
            <RouterLink class="hover:underline" to="/register">
            Register
            </RouterLink> 
          </p>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
</style>
