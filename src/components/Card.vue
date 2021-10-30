<template>
  <div class="card m-3">
    <img
      :src="image.urls.small"
      class="card-img-top"
      :alt="image.alt_description"
    />
    <div class="card-body">
      <h5 class="card-title">
        {{ image.header }}
      </h5>
      <p class="card-text">
        {{ image.data }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["image"],
};
</script>

<style>
.card {
  width: 18rem;
  height: 35rem;
  overflow: auto;
  cursor: pointer;
  transition: 0.5s all ease;
  background: #f0e6dd;
}

.card:hover {
  box-shadow: 0 5px 15px #75b7ba;
}

.card-img-top {
  width: 100%;
  height: 17rem;
}

.card-title {
  font-weight: 600;
}

.card-text {
  text-align: left;
}
</style>