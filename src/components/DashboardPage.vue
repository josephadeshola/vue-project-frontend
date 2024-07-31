<template>
  <div>
    <!-- Overlay -->

    <SideBar />
    <div class="p-4 sm:ml-64">
      <div class="p-4 mt-12">
        <div v-if="loading" class="flex justify-center items-center h-screen">
          Loading...
        </div>
         <div v-if="userJobs.length === 0" class="text-center mt-10">
            <p class="text-gray-600 text-xl">You have not posted any jobs yet.</p>
            <p class="text-gray-500">Start by posting a new job to see it here.</p>
          </div>
        <div v-else class="md:grid grid-cols-3 md:gap-4">
          <div
            v-for="job in userJobs"
            :key="job.id"
            class="md:px-6 mt-4 px-5 md:mt-0 py-6 shadow-md rounded bg-white"
          >
            <div class="flex gap-5">
              <img
                src="https://img.freepik.com/premium-photo/best-logo-template-vector-icon-illustration-design-ai-generated_966797-13127.jpg?w=740"
                class="h-10 rounded"
                alt=""
              />
              <div>
                <p class="font-bold text-sm">{{ job.companyName }} Ltd.</p>
                <p class="text-sm">{{ job.location }}</p>
              </div>
            </div>
            <p class="font-bold mt-2 text-md">{{ job.title }}</p>
            <p class="text-sm text-blue-700 py-2 font-bold">
              {{ job.jobType }}
            </p>
            <div class="text-sm">{{ job.requirement }}</div>
            <div class="gap-10 mt-5">
              <p class="font-bold mb-4 text-xl">
                ${{ job.salary
                }}<span class="text-sm font-light">/monthly</span>
              </p>
              <div class=" flex gap-3 justify-center">
              <RouterLink
                :to="{ name: 'JobDetails', params: { id: job.id } }"
                class="bg-blue-700 px-4 py-2 rounded-md text-sm md:text-[12px] transition hover:text-blue-700 hover:shadow-md hover:bg-white duration-300 text-white font-medium"
              >
                Edit Post
              </RouterLink>
              <RouterLink
                :to="{ name: 'JobDetails', params: { id: job.id } }"
                class="bg-red-500 px-4 py-2 rounded-md text-sm md:text-[12px] transition hover:text-red-700 hover:shadow-md hover:bg-white duration-300 text-white font-medium"
              >
                Delete Post
              </RouterLink>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import SideBar from "../components/SideBar.vue";
import axios from "axios";
import { ref, onMounted } from "vue";
import SideBarVue from "./SideBar.vue";

const userJobs = ref([]);
const loading = ref(true);
const errorMessage = ref(null);

const fetchUserJobs = async () => {
  const userId = JSON.parse(localStorage.getItem("user"));

  try {
    const response = await axios.get(
      `http://127.0.0.1:8000/api/jobs/user/${userId.id }`
    );
    userJobs.value = response.data.jobs
  } catch (error) {
    if (error.response && error.response.status === 404) {
      userJobs.value = [];
      errorMessage.value = 'You have not posted any jobs yet.';
    } else {
      console.error("Error fetching user jobs:", error);
      errorMessage.value = 'An error occurred while fetching your jobs. Please try again later.';
    }
  } finally {
    loading.value = false;
  }
};

onMounted(fetchUserJobs);
</script>
<style scoped>
</style>
