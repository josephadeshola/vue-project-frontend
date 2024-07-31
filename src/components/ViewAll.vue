<template>
        <div class="md:grid grid-cols-3 md:gap-4">
        <div v-for="job in jobs" :key="job.id" class="md:px-6 mt-4 px-5 md:mt-0 py-6 shadow-md rounded bg-white">
          <div class="flex gap-5">
            <img
              src="https://img.freepik.com/premium-photo/best-logo-template-vector-icon-illustration-design-ai-generated_966797-13127.jpg?w=740"
              class="h-10 rounded"
              alt=""
            />
            <div>
              <p class="font-bold text-sm">{{job.companyName}} Ltd.</p>
              <p class="text-sm">{{job.location}}</p>
            </div>
          </div>
          <p class="font-bold mt-2 text-md">{{ job.title }}</p>
          <p class="text-sm text-blue-700 py-2 font-bold">{{job.jobType}}</p>
          <div class="text-sm">{{job.requirement}}</div>
          <div class="flex gap-10 mt-5">
            <p class="font-bold text-xl">
              ${{job.salary}}<span class="text-sm font-light">/monthly</span>
            </p>
            <button
              class="bg-blue-700 px-4 py-2 rounded-md text-sm md:text-[12px] transition hover:text-blue-700 hover:shadow-md hover:bg-white duration-300 text-white font-medium"
            >
              Job Details
            </button>
          </div>
        </div> 
        </div>
</template>

<script setup>
import axios from "axios"
import { ref, onMounted } from "vue";

const jobs = ref([]);
const fetchJobs = async () => {
     const token = localStorage.getItem("token");
    
  try {
    const response = await axios.get("http://127.0.0.1:8000/api/jobs");
    console.log(response);
    jobs.value = response.data.jobs;
  } catch (error) {
    console.error("Error fetching jobs:", error);
  }
};
onMounted(fetchJobs);
</script>


<style>

</style>