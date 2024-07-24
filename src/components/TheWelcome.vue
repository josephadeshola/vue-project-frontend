<script setup>
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'

import { ref } from "vue";

const jobCategories = ref([
  { name: "Software Development", count: 376 },
  { name: "Accounting/Finance", count: 305 },
  { name: "Production/Operations", count: 95 },
  { name: "Design/Creative", count: 93 },
  { name: "Telecommunication", count: 450 },
  { name: "Markrting/Sales", count: 666 },
  { name: "Engineer/Architects", count: 376 },
  { name: "CyberSecurity", count: 37 },
  { name: "Data Science", count: 396 },
]);
</script>

<template>
  <div class="">
    <nav class="!bg-white border-gray-200 fixed w-full shadow-md z-10">
      <div
        class="flex flex-wrap justify-between items-center mx-auto max-w-screen-xl p-4"
      >
        <a
          href="https://flowbite.com"
          class="flex items-center space-x-3 rtl:space-x-reverse"
        >
          <img
            src="https://flowbite.com/docs/images/logo.svg"
            class="h-8"
            alt="Flowbite Logo"
          />
          <span
            class="self-center text-2xl font-semibold whitespace-nowrap dark:text-black"
            >JobList</span
          >
        </a>
        <div class="flex items-center space-x-6 rtl:space-x-reverse">
          <RouterLink to="/register" class="text-sm hover:underline text-black"
            >Register</RouterLink
          >
          <a
            href="#"
            class="text-sm text-blue-600 dark:text-blue-500 hover:underline"
            >Login</a
          >
        </div>
      </div>
    </nav>
    <div class="relative pt-16">
      <img
        class="w-full object-cover h-screen"
        src="https://img.freepik.com/premium-photo/serious-team-professionals-multiethnic-business-people-negotiating-modern-meeting-room_484651-23333.jpg?w=740"
        alt=""
      />
      <div
        class="absolute top-0 left-0 w-full h-full bg-black bg-opacity-50 flex items-center justify-center z-0"
      >
        <div class="text-white text-center px-3">
          <h1 class="text-4xl font-bold">
            Find Great Jobs to Build Your Bright Career
          </h1>
          <p class="mt-4">
            Explore opportunities that match your skills and aspirations.
          </p>
          <div class="borde flex gap-2">
            <input
              type="text"
              id="success"
              class="bg-blue-50 mt-4 py-4 border border-blue-500 text-black placeholder-blue-700 dark:placeholder-blue-500 text-sm rounded-md focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:border-blue-500"
              placeholder="Job title or keywords"
            />
            <input
              type="text"
              id="success"
              class="bg-blue-50 mt-4 py-4 border border-blue-500 text-black placeholder-blue-700 dark:placeholder-blue-500 text-sm rounded-md focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:border-blue-500"
              placeholder="Choose city"
            />
            <input
              type="text"
              id="success"
              class="bg-blue-50 mt-4 py-4 border border-blue-500 text-black placeholder-blue-700 dark:placeholder-blue-500 text-sm rounded-md focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:border-blue-500"
              placeholder="Category"
            />
            <button
              type="button"
              class="text-white bg-blue-700 w-10 h-10 mt-6 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm p-2.5 text-center inline-flex items-center me-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
            >
              <i class="bi bi-search text-xl font-bold"></i>
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="text-center bg-blue-700 py-7 -mt-10">
      <p class="md:text-4xl text-md text-white font-semibold mt-6">
        Unlock Your Career Potential
      </p>
      <p class="text-md text-white">
        Discover the perfect job opportunity for you.
      </p>
    </div>

    <p class="text-center font-bold text-2xl mt-10">Popular Category</p>
    <div class="text-center mx-auto flex justify-center">
      <div class="bg-black h-1 w-52"></div>
    </div>
    <div class="mx-auto grid md:grid-cols-3 md:px-32 gap-3 px-5 mt-5 md:mt-10">
      <div
        class="border boder-2 text-center shadow cursor-pointer hover:bg-blue-600 hover:font-bold text-md transition duration-300 hover:text-white py-3 rounded"
        v-for="category in jobCategories"
        :key="category.name"
      >
        {{ category.name }} ({{ category.count }})
      </div>
    </div>
    <div class="md:mt-20 mx-auto  bg-gray-100">
      <p class="font-bold text-2xl text-center pt-12">Recent Job Circulars</p>
      <div class=" md:grid grid-cols-3 px-3  py-7 md:px-44 md:gap-x-5">
      <div class="px-6 py-6 shadow-md rounded bg-white">
        <div class="flex gap-5">
          <img
            src="https://img.freepik.com/premium-photo/best-logo-template-vector-icon-illustration-design-ai-generated_966797-13127.jpg?w=740"
            class="h-10 rounded"
            alt=""
          />
          <div>
            <p class="font-bold text-sm">Darkento Ltd.</p>
            <p class="text-sm">New York,USA</p>
          </div>
        </div>
        <p class="font-bold mt-2 text-md">Front-end Developer</p>
        <p class="text-sm text-green-500 py-2 font-bold">Full-time</p>
        <div class="text-sm">CSS3,HTML5,javascript,Bootstrap,jQuery</div>
        <div class="flex gap-10 mt-5">
          <p class="font-bold text-xl">
            $5000<span class="text-sm font-light">/monthly</span>
          </p>
          <button
            class="bg-green-500 px-4 py-2 rounded-md text-md transition hover:text-green-500 hover:shadow-md hover:bg-white duration-300 text-white font-medium"
          >
            Apply Now
          </button>
        </div>
      </div>
      <div class="px-6 py-6 shadow-md mt-3 md:mt-0 rounded bg-white">
        <div class="flex gap-5">
          <img
            src="https://img.freepik.com/premium-photo/best-logo-template-vector-icon-illustration-design-ai-generated_966797-13127.jpg?w=740"
            class="h-10 rounded"
            alt=""
          />
          <div>
            <p class="font-bold text-sm">Darkento Ltd.</p>
            <p class="text-sm">New York,USA</p>
          </div>
        </div>
        <p class="font-bold mt-2 text-md">Front-end Developer</p>
        <p class="text-sm text-green-500 py-2 font-bold">Full-time</p>
        <div class="text-sm">CSS3,HTML5,javascript,Bootstrap,jQuery</div>
        <div class="flex gap-10 mt-5">
          <p class="font-bold text-xl">
            $5000<span class="text-sm font-light">/monthly</span>
          </p>
          <button
            class="bg-green-500 px-4 py-2 rounded-md text-md transition hover:text-green-500 hover:shadow-md hover:bg-white duration-300 text-white font-medium"
          >
            Apply Now
          </button>
        </div>
      </div>
      <div class="px-6 py-6 shadow-md mt-3 md:mt-0 rounded bg-white">
        <div class="flex gap-5">
          <img
            src="https://img.freepik.com/premium-photo/best-logo-template-vector-icon-illustration-design-ai-generated_966797-13127.jpg?w=740"
            class="h-10 rounded"
            alt=""
          />
          <div>
            <p class="font-bold text-sm">Darkento Ltd.</p>
            <p class="text-sm">New York,USA</p>
          </div>
        </div>
        <p class="font-bold mt-2 text-md">Front-end Developer</p>
        <p class="text-sm text-green-500 py-2 font-bold">Full-time</p>
        <div class="text-sm">CSS3,HTML5,javascript,Bootstrap,jQuery</div>
        <div class="flex gap-10 mt-5">
          <p class="font-bold text-xl">
            $5000<span class="text-sm font-light">/monthly</span>
          </p>
          <button
            class="bg-green-500 px-4 py-2 rounded-md text-md transition hover:text-green-500 hover:shadow-md hover:bg-white duration-300 text-white font-medium"
          >
            Apply Now
          </button>
        </div>
      </div>
    </div>
    </div>
  </div>
</template>
