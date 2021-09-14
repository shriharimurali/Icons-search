<template>
  <div class="overflow-auto">
    <b-pagination
      v-model="currentPage"
      :total-rows="total"
      :per-page="50"
      first-text="First"
      prev-text="Prev"
      next-text="Next"
      last-text="Last"
      class="justify-content-center"
      @change="handlePageChange"
    ></b-pagination>
  </div>
</template>

<script>
export default {
  props: {
    currentPage: {
      type: Number,
      required: true,
    },
    total: {
      type: Number,
      required: true,
    },
    handlePageChange: {
      type: Function,
      required: true,
    },
  },
};
</script>

<style lang="scss">
</style>
