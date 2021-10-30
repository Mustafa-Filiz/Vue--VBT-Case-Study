<template>
  <Form @form-submit="fetchRandomImages" />
</template>

<script>
import axios from "axios";
import RandExp from "randexp";
import Form from "./components/Form.vue";

export default {
  name: "App",
  components: {
    Form,
  },
  data() {
    return {
      images: [],
    };
  },
  methods: {
    fetchRandomImages: async function (amount) {
      await axios
        .get(
          `https://api.unsplash.com/photos/random?count=${amount}&client_id=SMLp9m3tYWy51OO-g1SO4nMDtPqyk97_szeF83DC9ck`
        )
        .then((res) => {
          this.images = res.data;
        });
      this.fetchRandomData();
      this.randomNumberGenerator();
    },
    fetchRandomData: async function () {
      let result;
      const options = {
        method: "GET",
        url: "https://ajith-messages.p.rapidapi.com/getMsgs",
        params: { category: "random" },
        headers: {
          "x-rapidapi-host": "ajith-messages.p.rapidapi.com",
          "x-rapidapi-key":
            "a6033c7d30mshef8ff9cced6c9d9p14992ejsn7a244e6bd1d7",
        },
      };
      for (let i = 0; i < this.images.length; i++) {
        result = await axios.request(options).then((res) => res.data.Message);
        this.images[i]["data"] = result;
      }
    },
    randomNumberGenerator() {
      let randomNumber;
      for (let i = 0; i < this.images.length; i++) {
        randomNumber = new RandExp(/^#[0-9]{4}$-Resim/).gen();
        this.images[i]["header"] = randomNumber;
      }
    },
  },
};
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
