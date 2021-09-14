<template>
  <div
    class="
      col-xs-12 col-sm-12 col-md-8 col-lg-5 col-xl-5 col-xxl-5
      mx-auto
      mt-n5
    "
  >
    <SearchAnime />
    <CommonText />
    <b-form
      class="search-form position-relative"
      @submit="onSubmit"
      @submit.prevent="true"
    >
      <b-form-input
        v-model="form.search"
        id="search"
        placeholder="Search Icon..."
        class="
          form-control
          search-input
          shadow-lg
          p-3
          mb-5
          bg-body
          col-xs-12 col-sm-12 col-md-10 col-lg-10 col-xl-10 col-xxl-10
        "
      ></b-form-input>
      <button class="search-button rounded-circle position-absolute">
        <img src="~assets/search.svg" alt="search icon" class="w-100" />
      </button>
    </b-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        search: "",
      },
    };
  },
  methods: {
    onSubmit() {
      this.$router.push({
        path: "/searchResults",
        query: { keyword: this.form.search },
      });
    },
  },
};
</script>


<style lang="scss">
.search-form {
  position: relative;
  justify-content: center;
  display: flex;
  .search-input {
    border-radius: 2rem;
    padding: 0 2rem;
    height: 60px;
    outline: none;
    border: 0;
    &:focus {
      box-shadow: none;
      border: 0;
    }
  }

  .search-button {
    width: 60px;
    height: 56px;
    border: 0;
    box-shadow: none;
    background-color: #6366f1;
    top: 2px;
    right: 3px;
    padding: 10px;
    text-align: center;

    @media (min-width: 768px) {
      right: 8.75%;
    }

    @media (min-width: 1200px) {
      right: 8.75%;
    }

    @media (min-width: 1400px) {
      right: 8.75%;
    }

    img {
      position: relative;
      top: -3px;
    }
  }
}
</style>
