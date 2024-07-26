<template>
  <SideBar />
  <div class="md:h-14 fixed w-full bg-white shadow-lg">
    <div class="flex justify-end gap-2 md:py-3 px-3">
      <p>Welcome:</p>
      <p class="text-blue-900 font-bold">Ayomide Adeshola</p>
    </div>
  </div>
  <div class="p-4 sm:ml-64">
    <p>CREATE JOB</p>
    <div class="min-h-screen flex py-7 items-center justify-center">
      <div class="bg-white p-8 rounded shadow-md max-w-xl w-full">
        <h2 class="text-2xl font-bold mb-6 text-center">Create Job Listing</h2>
        <form @submit.prevent="submitForm" class="space-y-6">
          <!-- Job Title -->
          <div class="flex gap-5 justify-between">
            <div class="w-full">
              <label for="title" class="block text-sm font-medium text-gray-700"
                >Job Title</label
              >
              <input
                id="title"
                v-model="form.title"
                name="title"
                type="text"
                class="mt-1 block w-full shadow-md px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                placeholder="Enter job title"
                required
              />
            </div>

            <!-- Company Name -->
            <div class="w-full">
              <label
                for="company"
                class="block text-sm font-medium text-gray-700"
                >Company Name</label
              >
              <input
                id="company"
                v-model="form.company"
                name="company"
                type="text"
                class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                placeholder="Enter company name"
                required
              />
            </div>
          </div>
          <!-- Location -->
          <div class="flex gap-5 justify-between">
            <div class="w-full">
              <label
                for="location"
                class="block text-sm font-medium text-gray-700"
                >Location</label
              >
              <input
                id="location"
                v-model="form.location"
                name="location"
                type="text"
                class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                placeholder="Enter job location"
                required
              />
            </div>

            <!-- Job Type -->
            <div class="w-full">
              <label
                for="jobType"
                class="block text-sm font-medium text-gray-700"
                >Job Type</label
              >
              <select
                id="jobType"
                v-model="form.jobType"
                name="jobType"
                class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                required
              >
                <option value="" disabled>Select job type</option>
                <option value="Full-time">Full-time</option>
                <option value="Part-time">Part-time</option>
                <option value="Contract">Contract</option>
              </select>
            </div>
          </div>

          <!-- Salary -->
          <div class="w-full">
            <label for="salary" class="block text-sm font-medium text-gray-700"
              >Salary</label
            >
            <input
              id="salary"
              v-model="form.salary"
              name="salary"
              type="number"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
              placeholder="Enter salary"
              required
            />
          </div>

          <!-- Description -->
          <div>
            <label
              for="description"
              class="block text-sm font-medium text-gray-700"
              >Description</label
            >
            <textarea
              id="description"
              v-model="form.description"
              name="description"
              rows="4"
              class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
              placeholder="Enter job description"
              required
            ></textarea>
          </div>

          <!-- Submit Button -->
          <div>
            <button
              type="submit"
              class="w-full px-4 py-2 bg-blue-600 text-white font-medium rounded-md shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500"
            >
              Create Job Listing
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
import SideBar from "../components/SideBar.vue";
import { ref } from "vue";

// Form data
const form = ref({
  title: "",
  company: "",
  location: "",
  jobType: "",
  salary: "",
  description: "",
});

// Method to handle form submission
const submitForm = () => {
  console.log("Form submitted", form.value);
  // Add your form submission logic here
};
</script>

<style scoped></style>
