<template>
  <div
    class="
      bg-background
      container-fluid
      flex-fill flex flex-column
      justify-content-center
      w-100
    "
  >
    <NavBar />
    <Loading v-if="loading" />
    <div class="row pt-5">
      <div
        class="
          col-xs-12 col-sm-12 col-md-10 col-lg-10 col-xl-10 col-xxl-10
          mx-auto
          mt-5
          p-1
        "
        v-if="!loading"
      >
        <h1 class="text-white pl-2 keyword-heading">
          {{ total }} {{ keyword }} icons
        </h1>
        <p class="text-white pl-2 mb-3 pr-5 description">
          Find & Download {{ total }} {{ keyword }} Icons in Line, Flat, Glyph,
          Colored Outline, and many more design styles for web, mobile, and
          graphic design projects. These royalty-free None Icon Images are
          available in PNG, SVG, AI, EPS, base64, and other formats &
          dimensions. Related Searches: Camera Icons Material Design Icons
          Google Material Icons Material Icons Icons Device Icons Focus Icons Ui
          Icons Battery Icons Bars Icons Charging Icons
        </p>
        <SearchFIlters :handleOk="handleOk" />
        <div class="search-result-box shadow-lg pt-5 pb-2 mb-5">
          <SearchItems :icons="icons" />
          <Pagination
            :currentPage="currentPage"
            :total="total"
            :handlePageChange="handlePageChange"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      response: null,
      icons: [],
      total: null,
      currentPage: 1,
      loading: false,
      keyword: this.$route.query.keyword,
    };
  },
  async fetch() {
    try {
      this.loading = true;
      const searchKey = this.$route.query.keyword;
      const options = {
        method: "GET",
        headers: new Headers({
          "Client-ID": "198175844506907",
        }),
      };
      const data = await fetch(
        `https://api.iconscout.com/v3/search?query=${searchKey}&product_type=item&asset=icon&price=free&per_page=50&page=${this.currentPage}&formats%5B%5D=svg&sort=relevant&styles%5B%5D=flat`,
        options
      ).then((res) => res.json());
      this.total = data.response.items.total;
      this.icons = data.response.items.data;
      this.loading = false;
    } catch (err) {
      this.loading = false;
      console.log("error in fetching icons===>", err);
    }
  },
  methods: {
    handlePageChange(value) {
      this.currentPage = value;
      this.$fetch();
    },
    handleFilterChange() {},
    handleOk() {
      alert(1);
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap");
body {
  font-family: "Roboto", sans-serif;
}
.bg-background {
  background-color: rgba(99, 102, 241, 1);
  .search-result-box {
    background-color: #fff;
    border-radius: 10px;
  }
  .keyword-heading {
    font-family: "Roboto", sans-serif;
    font-weight: 700;
    text-transform: capitalize;
  }
  .description {
    font-family: "Roboto", sans-serif;
    font-weight: 500;
  }
}
</style>
