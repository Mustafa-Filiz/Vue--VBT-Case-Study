<template>
  <div class="d-flex flex-column align-items-center">
    <input
      class="searchbar"
      type="text"
      placeholder="Search for a heading"
      v-model="searchText"
    />
    <div class="d-flex flex-wrap justify-content-center">
      <Card v-for="image in filteredImages" :key="image.id" :image="image" />
    </div>
    <!-- pagination -->
  </div>
</template>

<script>
import Card from "./Card.vue";

export default {
  name: "ResultArea",
  components: {
    Card,
  },
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
  computed: {
    filteredImages() {
      return this.images.filter((image) =>
        image.header?.toLowerCase().includes(this.searchText.toLowerCase())
      );
    },
  },
};
</script>

<style>
</style>