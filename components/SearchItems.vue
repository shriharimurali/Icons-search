<template>
  <ul
    id="search-list"
    class="d-flex flex-row mx-auto p-0 flex-wrap justify-content-center"
  >
    <li
      v-for="icon in icons"
      :key="icon.id"
      class="
        d-flex
        flex-column
        pt-2
        pr-5
        pl-5
        pb-2
        rounded
        justify-content-center
        rounded
      "
    >
      <b-img class="image" :src="icon.urls.png_64" :alt="icon.asset" />
      <p class="text-center mt-3 text-wrap mx-auto">{{ icon.name }}</p>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    icons: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="scss">
#search-list {
  list-style: none;
  li {
    min-height: 184px;
    cursor: pointer;
    transition: box-shadow 0.2s ease-in;
    &:hover {
      box-shadow: 0 0 0 1px #d8dbeb;
    }
  }
  p {
    width: 6rem;
    font-weight: 500;
    color: rgba(0, 0, 0, 0.65);
  }
}
</style>
