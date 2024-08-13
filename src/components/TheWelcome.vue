<script setup>
import WelcomeItem from "./WelcomeItem.vue";
import DocumentationIcon from "./icons/IconDocumentation.vue";
import ToolingIcon from "./icons/IconTooling.vue";
import EcosystemIcon from "./icons/IconEcosystem.vue";
import CommunityIcon from "./icons/IconCommunity.vue";
import SupportIcon from "./icons/IconSupport.vue";
import ViewAll from "../components/ViewAll.vue";
import { ref } from "vue";
import axios from "axios";
import { useRouter } from "vue-router";
import NavbarPageVue from "../components/NavbarPage.vue";
import { useToast } from "vue-toastification";

const router = useRouter();
const jobCategories = ref([
  { name: "Software Development", count: 376 },
  { name: "Accounting/Finance", count: 305 },
  { name: "Production/Operations", count: 95 },
  { name: "Design/Creative", count: 93 },
  { name: "Telecommunication", count: 450 },
  { name: "Marketing/Sales", count: 666 },
  { name: "Engineer/Architects", count: 376 },
  { name: "CyberSecurity", count: 37 },
  { name: "Data Science", count: 396 },
]);
const jobs = ref([]);
const filteredJobs = ref([]);
const query = ref("");
const location = ref("");
const loading = ref(false);
const toast = useToast();

const searchJobs = async () => {
  loading.value = true;
  try {
    if (!query.value && !location.value) {
      toast.warning("Please enter a job title or location to search..");
      return;
    }

    const response = await axios.get("http://127.0.0.1:8000/api/jobs");
    const jobsData = response.data.jobs;

    if (!jobsData || jobsData.length === 0) {
      console.log("No jobs found");
      return;
    }

    filteredJobs.value = jobsData.filter((job) => {
      const isTitleMatch =
        query.value === "" ||
        job.title.toLowerCase().includes(query.value.toLowerCase());
      const isLocationMatch =
        location.value === "" ||
        job.location.toLowerCase().includes(location.value.toLowerCase());
      return isTitleMatch && isLocationMatch;
    });

    if (filteredJobs.value.length === 0) {
      alert("No jobs found for the given search criteria.");
      return;
    }

    console.log(filteredJobs.value);
    router.push({
      name: "SearchResult",
      query: { jobs: JSON.stringify(filteredJobs.value) },
    });
  } catch (error) {
    console.error("Error fetching jobs:", error);
  } finally {
    loading.value = false;
  }
};
</script>



<template>
  <div>
    <div v-if="loading" class="flex justify-center items-center h-screen">
      <div class="loader16">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
    <div v-else>
      <NavbarPageVue />
      <div class="relative pt-16">
        <img
          class="w-full object-cover md:h-screen h-96"
          src="https://img.freepik.com/premium-photo/serious-team-professionals-multiethnic-business-people-negotiating-modern-meeting-room_484651-23333.jpg?w=740"
          alt=""
        />
        <div
          class="absolute top-0 left-0 w-full h-full bg-black bg-opacity-50 flex items-center justify-center z-0"
        >
          <div class="text-white text-center px-3">
            <h1 class="md:text-4xl text-2xl font-bold">
              Find Great Jobs to Build Your Bright Career
            </h1>
            <p class="mt-4">
              Explore opportunities that match your skills and aspirations.
            </p>
            <div class="borde flex gap-2">
              <input
                type="text"
                v-model="query"
                id="job-title"
                class="bg-blue-50 mt-4 py-4 border border-blue-500 text-black placeholder-blue-700 dark:placeholder-blue-500 text-sm rounded-md focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:border-blue-500"
                placeholder="Job title or keywords"
              />
              <input
                type="text"
                v-model="location"
                id="city"
                class="bg-blue-50 mt-4 py-4 border border-blue-500 text-black placeholder-blue-700 dark:placeholder-blue-500 text-sm rounded-md focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:border-blue-500"
                placeholder="Choose location"
              />
              <button
                @click="searchJobs"
                type="button"
                class="text-white bg-blue-700 w-56 h-12 mt-5 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm p-2.5 text-center inline-flex items-center me-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
              >
                <i class="bi bi-search text-xl font-bold"></i>
                <p class="text-md ms-1">search</p>
              </button>
            </div>
          </div>
        </div>
      </div>

      <div class="text-center bg-blue-600 md:hidden block py-7">
        <p class="md:text-4xl text-xl text-white font-semibold">
          Unlock Your Career Potential
        </p>
        <p class="text-md text-white">
          Discover the perfect job opportunity for you.
        </p>
      </div>
      <div class="relative container-fluid md:top-3 md:block hidden -top-2">
        <svg xmlns="http://www.w3.org/2000/svg" class="" viewBox="0 0 1440 320">
          <path
            fill="#73c2fb"
            fill-opacity="1"
            d="M0,128L34.3,144C68.6,160,137,192,206,224C274.3,256,343,288,411,288C480,288,549,256,617,256C685.7,256,754,288,823,282.7C891.4,277,960,235,1029,234.7C1097.1,235,1166,277,1234,293.3C1302.9,309,1371,299,1406,293.3L1440,288L1440,0L1405.7,0C1371.4,0,1303,0,1234,0C1165.7,0,1097,0,1029,0C960,0,891,0,823,0C754.3,0,686,0,617,0C548.6,0,480,0,411,0C342.9,0,274,0,206,0C137.1,0,69,0,34,0L0,0Z"
          ></path>
        </svg>
      </div>
      <div class="relative container-fluid md:-mt-80 md:block hidden -mt-32">
        <div class="text-center h-auto flex justify-center items-center">
          <div class="absolute md:top-10">
            <p class="md:text-4xl py-3 text-md text-white font-semibold mt-6">
              Unlock Your Career Potential
            </p>
            <p class="text-xl text-white">
              Discover the perfect job opportunity for you.
            </p>
          </div>
        </div>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320">
          <path
            fill="#1f75fe"
            fill-opacity="1"
            d="M0,128L34.3,144C68.6,160,137,192,206,224C274.3,256,343,288,411,288C480,288,549,256,617,256C685.7,256,754,288,823,282.7C891.4,277,960,235,1029,234.7C1097.1,235,1166,277,1234,293.3C1302.9,309,1371,299,1406,293.3L1440,288L1440,0L1405.7,0C1371.4,0,1303,0,1234,0C1165.7,0,1097,0,1029,0C960,0,891,0,823,0C754.3,0,686,0,617,0C548.6,0,480,0,411,0C342.9,0,274,0,206,0C137.1,0,69,0,34,0L0,0Z"
          ></path>
        </svg>
      </div>
      <p class="text-center font-bold text-2xl mt-10">Popular Category</p>
      <div class="text-center mx-auto flex justify-center">
        <div class="bg-black h-1 w-52"></div>
      </div>
      <div
        class="mx-auto grid md:grid-cols-3 md:px-32 gap-3 px-5 mt-5 md:mt-10"
      >
        <div
          class="border boder-2 text-center shadow cursor-pointer hover:bg-blue-600 hover:font-bold text-md transition duration-300 hover:text-white py-3 rounded"
          v-for="category in jobCategories"
          :key="category.name"
        >
          {{ category.name }} ({{ category.count }})
        </div>
      </div>

      <div class="md:px-44 pb-14 md:mt-20 mx-auto py-7 px-4 mt-7 bg-gray-100">
        <p class="font-bold text-2xl mb-5 text-center">Recent Job Circulars</p>
        <ViewAll />
      </div>
    </div>
    <footer class="bg-gray-800 text-white py-8">
      <div class="container mx-auto px-4">
        <div class="flex flex-wrap justify-between">
          <div class="w-full md:w-1/3 mb-6 md:mb-0">
            <h5 class="font-bold text-lg mb-2">Company Name</h5>
            <p class="text-gray-400">Address: 123 Main Street, City, State</p>
            <p class="text-gray-400">Email: josephay125d@gmail.com</p>
            <p class="text-gray-400">Phone: +234 8069697526</p>
          </div>

          <div class="w-full md:w-1/3 mb-6 md:mb-0">
            <h5 class="font-bold text-lg mb-2">Quick Links</h5>
            <ul class="list-none">
              <li class="mb-1">
                <a href="#" class="text-gray-400 hover:text-white">Home</a>
              </li>
              <li class="mb-1">
                <a href="#" class="text-gray-400 hover:text-white">About Us</a>
              </li>
              <li class="mb-1">
                <a href="#" class="text-gray-400 hover:text-white">Jobs</a>
              </li>
              <li class="mb-1">
                <a href="#" class="text-gray-400 hover:text-white">Contact</a>
              </li>
              <li>
                <a href="#" class="text-gray-400 hover:text-white"
                  >Privacy Policy</a
                >
              </li>
            </ul>
          </div>

          <div class="w-full md:w-1/3">
            <h5 class="font-bold text-lg mb-2">Follow Us</h5>
            <div class="flex space-x-4">
              <a
                href="#"
                aria-label="Facebook"
                class="text-gray-400 hover:text-white"
                ><i class="fab fa-facebook-f">Face Book</i></a
              >
              <a
                href="#"
                aria-label="Twitter"
                class="text-gray-400 hover:text-white"
                ><i class="fab fa-twitter">Linkedin</i></a
              >
              <a
                href="#"
                aria-label="LinkedIn"
                class="text-gray-400 hover:text-white"
                ><i class="fab fa-linkedin-in">Twitter</i></a
              >
              <a
                href="#"
                aria-label="Instagram"
                class="text-gray-400 hover:text-white"
                ><i class="fab fa-instagram">Instagram</i></a
              >
            </div>
          </div>
        </div>

        <div class="mt-8 border-t border-gray-700 pt-4">
          <p class="text-center text-gray-500">
            &copy; {{ new Date().getFullYear() }} Company Name. All rights
            reserved.
          </p>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
.loader16 {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  width: 100%;
}

.loader16 span {
  height: 20px;
  width: 20px;
  margin: 4px;
  border-radius: 10px;
  background-color: #a29bfe;
  animation: loader16-animation 1.5s infinite ease-in-out;
}

.loader16 span:last-child {
  margin-right: 0;
}

.loader16 span:nth-child(1) {
  animation-delay: -0.3s;
}

.loader16 span:nth-child(2) {
  animation-delay: -0.1s;
}

.loader16 span:nth-child(3) {
  animation-delay: 0.1s;
}

@keyframes loader16-animation {
  0% {
    transform: scale(0.8);
    background-color: #4236ec;
    box-shadow: 0 0 0 0 rgba(70, 60, 211, 0.7);
  }

  50% {
    transform: scale(1.2);
    background-color: #6c5ce7;
    box-shadow: 0 0 0 10px rgba(108, 92, 231, 0);
  }

  100% {
    transform: scale(0.8);
    background-color: #473ce4;
    box-shadow: 0 0 0 0 rgba(162, 155, 254, 0.7);
  }
}
</style>
