<template>
  <div>
    <div class="w-100 d-flex justify-content-end">
      <b-button
        v-b-modal.my-modal
        class="mb-3 align-self-end"
        id="filters-button"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="16"
          height="16"
          fill="currentColor"
          class="bi bi-filter-left"
          viewBox="0 0 16 16"
        >
          <path
            d="M2 10.5a.5.5 0 0 1 .5-.5h3a.5.5 0 0 1 0 1h-3a.5.5 0 0 1-.5-.5zm0-3a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 0 1h-7a.5.5 0 0 1-.5-.5zm0-3a.5.5 0 0 1 .5-.5h11a.5.5 0 0 1 0 1h-11a.5.5 0 0 1-.5-.5z"
          />
        </svg>
        Filters
      </b-button>
    </div>
    <b-modal id="my-modal" hide-header @ok="handleOk">
      <div class="row">
        <div
          class="
            col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12 col-xxl-12
            mb-4
          "
        >
          <p>Prodcut:</p>
          <vSelect :options="FILTERS.PRODUCT_TYPE" />
        </div>
        <div
          class="
            col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12 col-xxl-12
            mb-4
          "
        >
          <p>Asset:</p>
          <vSelect :options="FILTERS.ASSET_TYPE" />
        </div>
        <div
          class="
            col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12 col-xxl-12
            mb-4
          "
        >
          <p>Price:</p>
          <vSelect :options="FILTERS.PRICE_TYPE" />
        </div>
        <div
          class="
            col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12 col-xxl-12
            mb-4
          "
        >
          <p>Sort By:</p>
          <vSelect multiple :options="FILTERS.SORT_TYPE" />
        </div>
        <div
          class="
            col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12 col-xxl-12
            mb-4
          "
        >
          <p>Format:</p>
          <vSelect multiple :options="FILTERS.FORMATS" />
        </div>
        <div
          class="
            col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12 col-xxl-12
            mb-5
          "
        >
          <p>Styles:</p>
          <vSelect multiple :options="FILTERS.STYLES" />
        </div>
      </div>
    </b-modal>
  </div>
</template>


<script>
import vSelect from "vue-select";
import FILTERS from "../constants/filters";
export default {
  components: {
    vSelect,
  },
  props: {
    handleOk: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      FILTERS,
    };
  },
};
</script>


<style lang="scss">
@import "vue-select/src/scss/vue-select.scss";
#filters-button {
  background-color: #fff;
  color: #6366f1;
}
</style>
