<script setup>
import { reactive } from "@vue/reactivity";

const emits = defineEmits(["toggle-contact"]);

function toggleNav() {
  nav.toggled = !nav.toggled;
}

const nav = reactive({
  toggled: false,
});
</script>

<template>
  <nav class="fixed">
    <div
      class="flex flex-wrap justify-between items-center mx-auto w-screen py-4 md:p-3 bg-slate-900 bg-opacity-50 border-b border-slate-800 backdrop-blur-lg"
    >
      <RouterLink to="/" class="font-bold text-xl flex self-center ml-5 md:ml-0"
        >🧑‍💻 <span class="text-white">Malek Hamza</span></RouterLink
      >
      <div class="block md:hidden">
        <button
          class="flex items-center px-3 py-2 mx-7 border rounded text-teal-200 border-primary hover:text-secondary hover:bg-primary hover:shadow-teal-800"
          v-on:click="toggleNav()"
        >
          <svg
            class="fill-current h-3 w-3"
            viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <title>Menu</title>
            <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z" />
          </svg>
        </button>
      </div>
      <div v-show="nav.toggled" class="block md:hidden" id="mobile-nav">
        <ul>
          <li class="w-screen my-4">
            <RouterLink
              to="/about"
              id="mobile-nav"
              class="transition ease-in-out delay-50 font-bold hover:text-primary m-1 p-2 rounded-md block"
              >About me</RouterLink
            >
          </li>
          <li class="w-screen my-4">
            <RouterLink
              to="/projects"
              id="mobile-nav"
              class="transition ease-in-out delay-50 font-bold hover:text-primary m-1 p-2 rounded-md block"
              >Projects</RouterLink
            >
          </li>
          <div id="btn-container" class="grid place-items-end">
            <button
              class="primary-button"
              v-on:click="toggleNav()"
              @click="$emit('toggle-contact')"
            >
              Contact
            </button>
          </div>
        </ul>
      </div>
      <div id="desktop-nav" class="md:w-auto hidden md:block">
        <ul class="flex md:flex-row">
          <li class="mx-5">
            <RouterLink
              to="/about"
              class="transition ease-in-out delay-50 font-bold hover:text-primary"
              >About me</RouterLink
            >
          </li>
          <li class="mx-5">
            <RouterLink
              to="/projects"
              class="transition ease-in-out delay-50 font-bold hover:text-primary"
              >Projects</RouterLink
            >
          </li>
        </ul>
      </div>
      <button
        class="primary-button hidden md:block"
        @click="$emit('toggle-contact')"
      >
        Contact
      </button>
    </div>
  </nav>
  <div class="container h-20 w-screen"></div>
</template>

<style scoped lang="scss">
$primary: rgb(45 212 191);
$secondary: #111827;
.active {
  color: $primary;
}

#mobile-nav {
  .active {
    color: $secondary;
    background: $primary;
  }
}
</style>
