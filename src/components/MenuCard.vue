<script setup lang="ts">
import { Menu } from "../types";

defineProps<{
  menu: Menu;
}>();

const addToCart = (e: any) => {
  e.preventDefault();
};
</script>

<template>
  <a
    href=""
    :aria-label="menu.title"
    class="shadow-xl bg-slate-900 rounded-lg block p-5 hover:scale-105 transition-all duration-300"
    @click="addToCart"
  >
    <div
      class="flex justify-center w-[70%] min-w-[110px] aspect-square object-cover mx-auto mt-[-70px] mb-8 rounded-full"
    >
      <img
        :src="menu.image"
        :alt="menu.title"
        loading="lazy"
        width="auto"
        height="auto"
        class="rounded-full w-full h-full shadow-xl shadow-slate-950"
      />
    </div>
    <div class="rounded-lg bg-slate-800 p-2">
      <h3 class="text-[15px] font-semibold text-white">{{ menu.title }}</h3>
      <p class="text-[13px] font-normal text-neutral-400">
        {{ menu.description }}
      </p>
    </div>
    <div class="flex items-center justify-between mt-5">
      <span class="text-white text-[14px]">NGN {{ menu.price }}</span>
      <button
        class="rounded-full p-2 bg-orange-700 hover:bg-orange-800"
        aria-label="add to cart button"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
          width="24"
          height="24"
        >
          <path
            d="M11 11V5H13V11H19V13H13V19H11V13H5V11H11Z"
            fill="#ffffff"
          ></path>
        </svg>
      </button>
    </div>
  </a>
</template>
