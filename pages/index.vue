<template>
  <div>
    <NavBar />
    <div
      class="
        bg-background
        container-fluid
        flex-fill flex flex-column
        justify-content-center
        w-100
        vh-100
      "
    >
      <Search />
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.bg-background {
  background-color: rgba(99, 102, 241, 1);
  width: 100%;
  align-items: center;
}
</style>
