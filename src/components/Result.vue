<template>
  <div class="relative">
    <div
      class="
        absolute
        inset-x-0
        -translate-y-1/2
        rounded-lg
        bg-[#3B3054] bg-shorten-desktop
        p-10
      "
    >
      <div class="flex flex-col md:flex-row gap-4">
        <input
          ref="inputLink"
          v-model="link"
          type="text"
          placeholder="https://google.com"
          class="rounded-xl p-4 md:w-5/6 outline-none"
          :class="{
            'focus:outline-none focus:ring-4 focus:ring-red-400': isError,
          }"
          @keyup.enter="shortenIt"
        />
        <button
          @click="shortenIt"
          class="
            rounded-lg
            md:w-1/6
            bg-[#29C7C7]
            hover:bg-[#9be3e2]
            p-4
            text-white
            font-semibold
          "
        >
          Shorten It!
        </button>
      </div>
      <div v-if="isError" class="absolute mt-2">
        <p class="text-red-400 text-sm italic">{{ message }}</p>
      </div>
    </div>
  </div>
  <div class="pt-32 md:pt-20 space-y-4" ref="results">
    <div
      class="
        flex flex-col
        md:flex-row
        gap-4
        justify-between
        md:items-center
        bg-white
        rounded-md
        p-5
        w-full
      "
      v-for="(result, index) in results"
      :key="index"
    >
      <div class="font-bold">{{ result.link }}</div>
      <hr class="border bg-[#2bd1d1]" />
      <div class="md:space-x-4 space-y-4 md:space-y-0">
        <span>{{ result.shortLink }}</span>
        <button
          class="
            text-white
            font-semibold
            px-8
            py-2
            rounded-lg
            hover:bg-[#9be3e2]
            w-full
            md:w-32
          "
          :class="result.status ? 'bg-[#3a3053]' : 'bg-[#2bd1d1]'"
          @click="copyURL(index, result.shortLink)"
          ref="copyBtn"
        >
          {{ result.status ? "Copied!" : "Copy" }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      link: "",
      results: [],
      message: "",
      isError: false,
    };
  },
  methods: {
    async shortenIt() {
      if (this.link !== "") {
        if (this.isValid(this.link)) {
          let shortLink = await this.shorten(this.link);
          this.results.push({
            link: this.link,
            shortLink: "https://rebrand.ly/" + shortLink,
            status: false,
          });
          this.link = ""
          this.$refs.inputLink.focus()
          return this.isError = false;
        } else {
          this.message = "Please add valid url";
        }
      } else {
        this.message = "Please add a link";
      }

      this.isError = true;

      this.$refs.inputLink.focus();
    },
    isValid(link) {
      let url = /^(https?):\/\/([a-z/d/.-]+).([a-z])(\.[a-z])?$/;
      return url.test(link);
    },
    async shorten(url) {
      const axios = require("axios");

      const headers = {
        "Content-Type": "application/json",
        apikey: "cbcaae4e35ee47a7af8cac20cf65c366",
      };

      let endpoint = "https://api.rebrandly.com/v1/links";
      let linkRequest = {
        destination: url,
        domain: { fullName: "rebrand.ly" },
      };
      const apiCall = {
        method: "post",
        url: endpoint,
        data: linkRequest,
        headers: headers,
      };
      let apiResponse = await axios(apiCall);
      return apiResponse.data.slashtag;
    },
    copyURL(id, url) {
      this.results[id].status = true;
      navigator.clipboard.writeText(url);
    }
  },
};
</script>

<style>
</style>