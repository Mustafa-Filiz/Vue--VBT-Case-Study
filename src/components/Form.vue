<template>
  <form
    class="d-flex flex-column align-items-center"
    @submit.prevent="$emit('formSubmit', amount)"
  >
    <label for="amount" id="label">Enter amount of random data:</label>
    <input
      id="amount"
      class="searchbar"
      v-model="amount"
      placeholder="Max. 30"
      list="options"
    />
    <datalist id="options">
      <option value="10"></option>
      <option value="20"></option>
      <option value="30"></option>
    </datalist>
  </form>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      amount: null,
    };
  },
};
</script>

<style>
#label {
  color: white;
  font-size: 1.3rem;
}
</style>