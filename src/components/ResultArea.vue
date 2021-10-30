<template>
  <div class="d-flex flex-column align-items-center">
    <input
      class="searchbar"
      type="text"
      placeholder="Search for a heading"
      v-model="searchText"
    />
    <div class="d-flex flex-wrap justify-content-center">
      <Card v-for="image in currentCards" :key="image.id" :image="image" />
    </div>
    <Pagination
      :cardsPerPage="cardsPerPage"
      :totalCards="filteredImages.length"
      @change-page="updatePage"
    />
  </div>
</template>

<script>
import Card from "./Card.vue";
import Pagination from "./Pagination.vue";

export default {
  name: "ResultArea",
  components: {
    Card,
    Pagination,
  },
  data() {
    return {
      searchText: "",
      currentPage: 1,
      cardsPerPage: 5,
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
    indexOfLastCard() {
      return this.currentPage * this.cardsPerPage;
    },

    indexOfFirstCard() {
      return this.indexOfLastCard - this.cardsPerPage;
    },

    currentCards() {
      return this.filteredImages.slice(
        this.indexOfFirstCard,
        this.indexOfLastCard
      );
    },
  },
  methods: {
    updatePage(page) {
      return (this.currentPage = page);
    },
  },
};
</script>

<style>
</style>