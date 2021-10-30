<template>
  <Form @form-submit="fetchRandomImages" />
</template>

<script>
import Form from "./components/Form.vue";

export default {
  name: 'App',
  components: {
    Form,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
    padding-top: 60px;
  width: 100%;
  min-height: 100vh;
  background: linear-gradient(
    110deg,
    rgba(63, 185, 132, 1) 0%,
    rgba(55, 120, 110, 1) 50%,
    rgba(49, 71, 94, 1) 100%
  );
}
</style>
