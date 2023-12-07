<script setup lang="ts">
import MenuCard from "../components/MenuCard.vue";
import Navbar from "../components/Navbar.vue";
import favourites from "../data/favourites";
import services from "../data/services";
import testimonials from "../data/testimonials";
import FooterBar from "../components/FooterBar.vue";
</script>

<template>
  <header>
    <Navbar />
    <section
      class="bg-slate-950/80 relative before:absolute before:w-full before:h-full before:bg-no-repeat before:bg-cover before:top-0 before:left-0 before:z-[-1] before:pointer-events-none before:bg-[url('https://res.cloudinary.com/dk9bt9lkn/image/upload/v1701862292/eats_n_treats/hero-mobile_xcti7w.jpg')] md:before:bg-[url('https://res.cloudinary.com/dk9bt9lkn/image/upload/v1701862294/eats_n_treats/hero-desktop_ibphwp.jpg')]"
    >
      <div
        class="max-w-[1000px] w-full m-auto p-4 sm:p-12 min-h-[calc(100vh-60px)] flex items-center gap-12"
      >
        <div
          class="w-full text-center md:text-left md:w-1/2 flex flex-col gap-8"
        >
          <h1 class="text-[35px] md:text-[45px] font-bold text-orange-500">
            Lorem ipsum dolor sit amet.
          </h1>
          <p class="text-neutral-300 text-[18px] sm:text-[20px] font-semibold">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit.
          </p>
          <RouterLink
            to="/"
            class="px-8 py-4 rounded-lg bg-orange-500 text-white w-fit m-auto md:m-0 hover:bg-orange-600"
            aria-label="view menu button"
          >
            View Menu
          </RouterLink>
        </div>
      </div>
    </section>
  </header>

  <main>
    <section>
      <div class="wrapper py-12">
        <h2
          class="text-[25px] sm:text-[25px] md:text-[35px] text-orange-500 font-bold text-center mb-24"
        >
          Customer Favourites
        </h2>
        <div
          class="grid grid-cols-1 min-[400px]:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-3 gap-y-[4.5rem]"
        >
          <MenuCard v-for="item in favourites" :key="item.id" :menu="item" />
        </div>
      </div>
    </section>

    <section>
      <div class="wrapper py-12">
        <h2
          class="text-[25px] sm:text-[25px] md:text-[35px] text-orange-500 font-bold text-center mb-20"
        >
          Our Services
        </h2>
        <div
          class="grid grid-cols-2 gap-4 sm:grid-cols-3 md:grid-cols-4 lg:gap-12 max-w-[900px] w-full m-auto"
        >
          <a
            v-for="item in services"
            :key="item.text"
            href=""
            :aria-label="item.text"
            class="bg-slate-900/50 px-4 py-6 rounded-3xl flex flex-col gap-4 items-center justify-center group hover:scale-105 transition-all duration-300"
          >
            <div
              class="max-w-[50px] mx-auto min-[480px]:max-w-[80px]"
              v-html="item.icon"
            ></div>
            <span
              class="text-[12px] min-[480px]:text-[14px] text-neutral-500 group-hover:text-orange-500 text-center font-semibold"
              >{{ item.text }}</span
            >
          </a>
        </div>
      </div>
    </section>

    <section>
      <div class="wrapper py-12 pb-28">
        <h2
          class="text-[25px] sm:text-[25px] md:text-[35px] text-orange-500 font-bold text-center mb-20"
        >
          Testimonials
        </h2>
        <div
          class="grid grid-cols-1 min-[400px]:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-3"
        >
          <div
            v-for="item in testimonials"
            :key="item.author"
            class="p-6 bg-slate-900 rounded-xl"
          >
            <div class="mb-2">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                width="50"
                height="50"
              >
                <path
                  d="M4.58341 17.3211C3.55316 16.2275 3 15 3 13.0104C3 9.51092 5.45651 6.37372 9.03059 4.82324L9.92328 6.20085C6.58804 8.00545 5.93618 10.3461 5.67564 11.8221C6.21263 11.5444 6.91558 11.4467 7.60471 11.5106C9.40908 11.6778 10.8312 13.1591 10.8312 15C10.8312 16.933 9.26416 18.5 7.33116 18.5C6.2581 18.5 5.23196 18.0096 4.58341 17.3211ZM14.5834 17.3211C13.5532 16.2275 13 15 13 13.0104C13 9.51092 15.4565 6.37372 19.0306 4.82324L19.9233 6.20085C16.588 8.00545 15.9362 10.3461 15.6756 11.8221C16.2126 11.5444 16.9156 11.4467 17.6047 11.5106C19.4091 11.6778 20.8312 13.1591 20.8312 15C20.8312 16.933 19.2642 18.5 17.3312 18.5C16.2581 18.5 15.232 18.0096 14.5834 17.3211Z"
                  class="fill-slate-950"
                ></path>
              </svg>
            </div>
            <p class="text-[14px] font-semibold text-slate-400 mb-4">
              {{ item.review }}
            </p>
            <p class="text-[14px] font-semibold text-slate-600 text-right">
              - {{ item.author }}
            </p>
          </div>
        </div>
      </div>
    </section>
  </main>

  <FooterBar />
</template>
