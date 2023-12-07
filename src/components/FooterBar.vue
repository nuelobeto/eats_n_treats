<script setup lang="ts">
import { RouterLink } from "vue-router";
import Logo from "../assets/logo.png";
</script>

<template>
  <footer class="bg-black">
    <section class="border-b-2 border-neutral-900">
      <div class="wrapper py-6 flex items-center justify-between">
        <RouterLink
          to="/"
          aria-label="Eats N Treats logo"
          class="flex items-center gap-2 text-white font-bold"
        >
          <img :src="Logo" alt="logo image" width="35" height="35" />
          <span>Eats N Treats</span>
        </RouterLink>

        <div class="flex items-center gap-8 text-[14px]">
          <RouterLink
            to="/"
            aria-label="Privacy"
            class="flex items-center gap-2 text-neutral-500 hover:text-white"
          >
            Privacy
          </RouterLink>
          <RouterLink
            to="/"
            aria-label="Terms"
            class="flex items-center gap-2 text-neutral-500 hover:text-white"
          >
            Terms
          </RouterLink>
        </div>
      </div>
    </section>
    <section>
      <div class="wrapper py-6">
        <p class="text-center text-[12px] text-neutral-500">
          Copyright ©️ Eats N treats. All rights reserved
        </p>
      </div>
    </section>
  </footer>
</template>
