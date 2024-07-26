<template>
  <div class="bg-slate-200 px-2 h-screen flex items-center justify-center">
    <div class="max-w-md w-full p-4 shadow-lg bg-white rounded">
      <p class="text-center font-bold text-3xl">Login Here</p>
      <div class="py-3 px-5">
        <hr class="text-blue-500" />
      </div>
      <form @submit.prevent="login" class="space-y-4">
        <div>
          <label for="email" class="block text-sm font-medium text-gray-700"
            >Email</label
          >
          <input
            id="email"
            v-model="$v.email.$model"
            name="email"
            type="email"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
            placeholder="Enter your email address"
          />
        </div>
        <div>
          <label
            for="password"
            class="block text-sm -mt-1 font-medium text-gray-700"
            >Password</label
          >
          <input
            id="password"
            v-model="$v.password.$model"
            name="password"
            type="password"
            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
            placeholder="Enter your password"
          />
        </div>
        <div>
          <button
            type="submit"
            class="w-full px-4 py-2 bg-blue-600 text-white font-medium rounded-md shadow-sm hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500"
          >
            Login
          </button>
          <p class="text-sm mt-2 text-center">
            Don't have an account?
            <RouterLink class="hover:underline" to="/register"
              >Register</RouterLink
            >
          </p>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>

import useVuelidate from "@vuelidate/core";
import { email, required } from "@vuelidate/validators";
import axios from "axios";
import { computed, ref } from "vue";
import { RouterLink, useRouter } from "vue-router";
import { useToast } from "vue-toastification";

const router = useRouter();
const form = ref({
  email: "",
  password: "",
});

const rules = computed(() => ({
  email: { required, email },
  password: { required },
}));

const $v = useVuelidate(rules, form);
const toast = useToast();

const login = async () => {
  if ($v.value.$invalid) {
    $v.value.$touch();
    toast.error("Please fill all the fields");
    return;
  }
  const userObject = {
    email: form.value.email,
    password: form.value.password,
  };

  try {
    const response = await axios.post(
      "http://127.0.0.1:8000/api/login",
      userObject
    );
    localStorage.setItem("token", response.data.token);
    localStorage.setItem("user", JSON.stringify(response.data.user));
    toast.success("Login successful!");
    setTimeout(() => {
      router.push("/dashboard")
    }, 4000);
  } catch (error) {
    console.error(error.response);
    if (error.response && error.response.status === 401) {
      toast.error("Incorrect email or password");
    } else {
      toast.error("An error occurred. Please try again later.");
    }
  }
};
</script>

<style></style>
