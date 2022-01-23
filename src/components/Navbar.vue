<template>
  <div class="px-6 md:px-40 py-10">
    <div
      class="
        relative
        flex
        justify-between
        items-center
        font-semibold
        text-[#BFBFBF]
        gap-8
      "
    >
      <img src="../assets/images/logo.svg" alt="" />
      <div class="hidden md:flex justify-between items-center gap-8 w-full">
        <div class="space-x-6">
          <a href="#" class="hover:text-[#34313c]">Features</a>
          <a href="#" class="hover:text-[#34313c]">Pricing</a>
          <a href="#" class="hover:text-[#34313c]">Resources</a>
        </div>

        <div class="space-x-6">
          <a href="#" class="hover:text-[#34313c]">Login</a>
          <button
            class="rounded-full bg-[#29C7C7] hover:bg-[#9be3e2] text-white px-6 py-2 font-semibold"
          >
            Sign Up
          </button>
        </div>
      </div>

      <!-- Mobile Nav -->
      <div class="md:hidden">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="currentColor"
          class="bi bi-list w-10 h-10"
          viewBox="0 0 16 16"
          @click="toggleMobileMenu"
        >
          <path
            fill-rule="evenodd"
            d="M2.5 12a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z"
          />
        </svg>

        <div
          class="absolute inset-x-0 rounded-xl mt-4 px-6 py-8 bg-[#3B3054]"
          v-if="mobileMenu"
        >
          <div class="flex flex-col items-center text-white space-y-8">
            <a href="#">Features</a>
            <a href="#">Pricing</a>
            <a href="#">Resources</a>
            <hr class="border border-[#BFBFBF] w-full rounded-full" />
            <a href="#">Login</a>
            <button
              class="
                rounded-full
                bg-[#29C7C7]
                text-white
                px-6
                py-2
                font-semibold
                w-full
              "
            >
              Sign Up
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mobileMenu: false,
    };
  },
  methods: {
    toggleMobileMenu() {
      this.mobileMenu = !this.mobileMenu;
    },
  },
};
</script>

<style>
</style>