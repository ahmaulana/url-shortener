<template>
  <section>
    <div class="px-6 md:px-40 pb-20 md:pb-40 bg-[#f0f1f6] space-y-10">
      <Result />
      <div class="pt-20">
        <div class="flex justify-center text-center mb-28">
          <div class="md:w-1/2 space-y-4">
            <h2 class="text-3xl md:text-4xl text-[#34313c] font-semibold">
              Advanced Statistics
            </h2>
            <p class="text-lg text-[#a09fa7]">
              Track how your links are performing across the web with our
              advanced statistics dashboard.
            </p>
          </div>
        </div>
        <div class="relative">
          <div
            class="
              grid grid-cols-1
              md:grid-cols-3
              gap-20
              md:gap-5
              items-stretch
              text-center
              md:text-left
            "
          >
            <div class="rounded-lg bg-white px-6 pb-8 z-10">
              <div class="flex flex-col items-center md:items-start">
                <div
                  class="
                    flex
                    justify-center
                    items-center
                    bg-[#3a3053]
                    w-20
                    h-20
                    rounded-full
                    -translate-y-1/2
                  "
                >
                  <img
                    src="../assets/images/icon-brand-recognition.svg"
                    class="w-10 h-10"
                  />
                </div>
              </div>
              <div class="text-2xl text-[#34313c] font-semibold mb-4">
                Brand recognition
              </div>
              <p class="text-[#a09fa7]">
                Boost your brand recognition with each click. Generic links
                don't mean a thing. Branded links help instil confidence in your
                content.
              </p>
            </div>
            <div class="rounded-lg bg-white px-6 pb-8 z-10 md:translate-y-10">
              <div class="flex flex-col items-center md:items-start">
                <div
                  class="
                    flex
                    justify-center
                    items-center
                    bg-[#3a3053]
                    w-20
                    h-20
                    rounded-full
                    -translate-y-1/2
                  "
                >
                  <img
                    src="../assets/images/icon-detailed-records.svg"
                    class="w-10 h-10"
                    alt=""
                  />
                </div>
              </div>
              <div class="text-2xl text-[#34313c] font-semibold mb-4">
                Detailed Records
              </div>
              <p class="text-[#a09fa7]">
                Gain insight into who is clicking your links. Knowing when and
                where people engage with your content helps inform better
                decisions.
              </p>
            </div>
            <div class="rounded-lg bg-white px-6 pb-8 z-10 md:translate-y-20">
              <div class="flex flex-col items-center md:items-start">
                <div
                  class="
                    flex
                    justify-center
                    items-center
                    bg-[#3a3053]
                    w-20
                    h-20
                    rounded-full
                    -translate-y-1/2
                  "
                >
                  <img
                    src="../assets/images/icon-fully-customizable.svg"
                    class="w-10 h-10"
                    alt=""
                  />
                </div>
              </div>
              <div class="text-2xl text-[#34313c] font-semibold mb-4">
                Fully Customizable
              </div>
              <p class="text-[#a09fa7]">
                Improve brand awareness and content discoverability through
                customizable links, supercharging audience engagement.
              </p>
            </div>
            <hr
              class="
                absolute
                w-2
                md:w-full
                bg-[#2ad1d2]
                h-full
                md:h-2
                self-center
                justify-self-center
              "
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Result from "./Result.vue"

export default {
  components: {
    Result
  },
  data() {
    return {
      link: "",
      validLink: "",
      message: "",
      isError: false,
    };
  },
  methods: {
    shortenIt() {
      if (this.link !== "") {
        if(this.isValid(this.link)){
          this.validLink = this.link
          return this.isError = false
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
      return url.test(link)
    },
  },
};
</script>

<style>
</style>