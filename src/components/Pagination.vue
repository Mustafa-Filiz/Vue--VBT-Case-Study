<template>
  <nav>
    <ul class="pagination">
      <li class="page-item" v-for="page in pageNumbers" :key="page">
        <a href="#" class="page-link" @click="$emit('changePage', page)">
          {{ page }}
        </a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "Pagination",
  props: ["cardsPerPage", "totalCards"],
  computed: {
    pageNumbers() {
      const pages = [];
      for (
        let i = 1;
        i <= Math.ceil(this.totalCards / this.cardsPerPage);
        i++
      ) {
        pages.push(i);
      }
      return pages;
    },
  },
};
</script>

<style>
ul {
  margin: 1rem;
}
</style>