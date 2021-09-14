<template>
  <div class="mt-5 w-75 mx-auto">
    <lottie :options="lottieOptions" @animCreated="handleAnimation" />
  </div>
</template>

<script>
import lottie from "vue-lottie/src/lottie.vue";
import * as animationData from "@/assets/search.json";

export default {
  components: {
    lottie,
  },
  data() {
    return {
      anim: null, // for saving the reference to the animation
      lottieOptions: { animationData: animationData.default },
    };
  },
  methods: {
    handleAnimation: function (anim) {
      this.anim = anim;
    },
  },
};
</script>

<style lang="scss">
</style>
