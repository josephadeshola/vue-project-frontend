<template>
<div class="bg-slate-200 h-screen py-5">
   <div class="max-w-md mx-auto p-4 shadow-lg bg-white rounded ">
    <p class="text-center font-bold text-3xl">Register</p>
    <div class="py-3 px-5">
    <hr class="text-blue-500">
    </div>
  <form class="space-y-4">
    <!-- Full Name -->
    <div>
      <label for="fullname" class="block text-sm font-medium text-gray-700">Full Name</label>
      <input
        id="fullname"
        name="fullname"
        type="text"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Enter your full name"
      />
    </div>

    <!-- Email -->
    <div>
      <label for="email" class="block text-sm fo -mt-2 nt-medium text-gray-700">Email</label>
      <input
        id="email"
        name="email"
        type="email"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Enter your email address"
      />
    </div>

    <!-- City -->
    <div>
      <label for="city" class="block text-sm fon -mt-2 t-medium text-gray-700">City</label>
      <input
        id="city"
        name="city"
        type="text"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Enter your city"
      />
    </div>

    <!-- State -->
    <div>
      <label for="state" class="block text-sm fo -mt-2 nt-medium text-gray-700">State</label>
      <input
        id="state"
        name="state"
        type="text"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Enter your state"
      />
    </div>

    <!-- Password -->
    <div>
      <label for="password" class="block text-sm -mt-2  font-medium text-gray-700">Password</label>
      <input
        id="password"
        name="password"
        type="password"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Enter your password"
      />
    </div>

    <!-- Confirm Password -->
    <div>
      <label for="confirm-password" class="block -mt-2  text-sm font-medium text-gray-700">Confirm Password</label>
      <input
        id="confirm-password"
        name="confirm-password"
        type="password"
        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="Confirm your password"
      />
    </div>

    <!-- Submit Button -->
    <div>
      <button
        type="submit"
        class="w-full px-4 py-2 bg-blue-600 text-white font-medium rounded-md shadow-sm hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500"
      >
        Submit
      </button>
      <p class="text-sm mt-2">Already have an account? 
        <RouterLink class="hover:underline" to="/login">
        Login
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