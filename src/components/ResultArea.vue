<template>
  <div class="d-flex flex-column align-items-center">
    <input
      class="searchbar"
      type="text"
      placeholder="Search for a heading"
      v-model="searchText"
    />
    <div class="d-flex flex-wrap justify-content-center">
      <!-- card -->
    </div>
    <!-- pagination -->
  </div>
</template>

<script>
export default {
  name: "ResultArea",
  data() {
    return {
      searchText: "",
    };
  },
  props: {
    images: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style>
</style>