<template>
  <div
    class="position-fixed w-100 d-flex align-items-center h-100"
    id="loading-box"
  >
    <lottie
      :options="lottieOptions"
      @animCreated="handleAnimation"
      :width="400"
      :height="400"
      class="top-50"
    />
  </div>
</template>

<script>
import lottie from "vue-lottie/src/lottie.vue";
import * as animationData from "@/assets/loading.json";

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
#loading-box {
  background-color: rgba(255, 255, 255, 0.5);
}
</style>
