<script setup lang="ts">
import { RouterLink } from "vue-router";
import Logo from "../assets/logo.png";
import navlinks from "../data/navlinks";
import { ref, onMounted, onBeforeUnmount, watch } from "vue";

const showMobileNavWrapper = ref(false);
const showMobileNav = ref(false);
let menuBtn: any, mobileNav: any;

const handleShowMobileNav = () => {
  showMobileNavWrapper.value = true;
  setTimeout(() => {
    showMobileNav.value = true;
  }, 50);
};

const handleCloseMobileNav = () => {
  showMobileNav.value = false;
  setTimeout(() => {
    showMobileNavWrapper.value = false;
  }, 150);
};

const closeMobileNav = (e: any) => {
  if (
    menuBtn &&
    mobileNav &&
    !menuBtn.contains(e.target) &&
    !mobileNav.contains(e.target)
  ) {
    showMobileNav.value = false;
  }
};

onMounted(() => {
  menuBtn = document.querySelector("#menu-btn");
  mobileNav = document.querySelector("#mobile-nav");

  window.addEventListener("click", closeMobileNav);
});

onBeforeUnmount(() => {
  window.removeEventListener("click", closeMobileNav);
});
</script>

<template>
  <nav class="w-full fixed top-0 left-0 bg-slate-950 z-10">
    <div class="wrapper h-[60px] flex items-center justify-between">
      <RouterLink
        to="/"
        aria-label="Eats N Treats logo"
        class="flex items-center gap-2 text-white font-bold"
      >
        <img :src="Logo" alt="logo image" width="35" height="35" />
        <span>Eats N Treats</span>
      </RouterLink>

      <div class="flex items-center justify-center gap-4 sm:hidden">
        <RouterLink to="/" aria-label="basket" class="group">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            width="24"
            height="24"
          >
            <path
              d="M12.0049 2C15.3186 2 18.0049 4.68629 18.0049 8V9H22.0049V11H20.8379L20.0813 20.083C20.0381 20.6013 19.6048 21 19.0847 21H4.92502C4.40493 21 3.97166 20.6013 3.92847 20.083L3.17088 11H2.00488V9H6.00488V8C6.00488 4.68629 8.69117 2 12.0049 2ZM18.8309 11H5.17788L5.84488 19H18.1639L18.8309 11ZM13.0049 13V17H11.0049V13H13.0049ZM9.00488 13V17H7.00488V13H9.00488ZM17.0049 13V17H15.0049V13H17.0049ZM12.0049 4C9.86269 4 8.1138 5.68397 8.00978 7.80036L8.00488 8V9H16.0049V8C16.0049 5.8578 14.3209 4.10892 12.2045 4.0049L12.0049 4Z"
              class="fill-white group-hover:fill-orange-500"
            ></path>
          </svg>
        </RouterLink>

        <button
          id="menu-btn"
          class="p-2 rounded-full hover:bg-slate-900"
          aria-label="menu button"
          @click="
            showMobileNav ? handleCloseMobileNav() : handleShowMobileNav()
          "
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            width="22"
            height="22"
          >
            <path
              d="M3 4H21V6H3V4ZM3 11H21V13H3V11ZM3 18H21V20H3V18Z"
              fill="#ffffff"
            ></path>
          </svg>
        </button>

        <div
          id="mobile-nav"
          class="w-full absolute top-full left-0 z-10"
          :class="[showMobileNavWrapper ? 'block' : 'hidden']"
        >
          <div
            class="w-full bg-slate-900 transition-all duration-300 h-auto shadow-xl"
            :class="[
              showMobileNav
                ? ' max-h-[300px] overflow-auto hide-scroll pointer-events-auto'
                : 'max-h-0 overflow-hidden pointer-events-none',
            ]"
          >
            <div class="p-4 flex flex-col gap-2">
              <RouterLink
                v-for="link in navlinks"
                to="/"
                :key="link.text"
                :aria-label="link.text"
                class="hover:bg-slate-800 px-3 py-2 rounded-lg flex items-center justify-center hover:text-orange-500 text-white text-[14px]"
              >
                {{ link.text }}
              </RouterLink>
              <RouterLink
                to="/"
                class="bg-orange-500 text-white py-2 px-4 rounded-lg hover:bg-orange-600 flex items-center justify-center text-[14px]"
                >Login</RouterLink
              >
            </div>
          </div>
        </div>
      </div>

      <div class="hidden sm:flex items-center gap-8 text-white text-[14px]">
        <RouterLink
          v-for="link in navlinks"
          to="/"
          :key="link.text"
          :aria-label="link.text"
          class="hover:text-orange-500"
        >
          {{ link.text }}
        </RouterLink>
        <RouterLink to="/" aria-label="basket" class="group">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            width="24"
            height="24"
          >
            <path
              d="M12.0049 2C15.3186 2 18.0049 4.68629 18.0049 8V9H22.0049V11H20.8379L20.0813 20.083C20.0381 20.6013 19.6048 21 19.0847 21H4.92502C4.40493 21 3.97166 20.6013 3.92847 20.083L3.17088 11H2.00488V9H6.00488V8C6.00488 4.68629 8.69117 2 12.0049 2ZM18.8309 11H5.17788L5.84488 19H18.1639L18.8309 11ZM13.0049 13V17H11.0049V13H13.0049ZM9.00488 13V17H7.00488V13H9.00488ZM17.0049 13V17H15.0049V13H17.0049ZM12.0049 4C9.86269 4 8.1138 5.68397 8.00978 7.80036L8.00488 8V9H16.0049V8C16.0049 5.8578 14.3209 4.10892 12.2045 4.0049L12.0049 4Z"
              class="fill-white group-hover:fill-orange-500"
            ></path>
          </svg>
        </RouterLink>
        <RouterLink
          to="/"
          aria-label="login button"
          class="bg-orange-500 text-white py-[6px] px-4 rounded-lg hover:bg-orange-600"
          >Login</RouterLink
        >
      </div>
    </div>
  </nav>
</template>
