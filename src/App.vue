<template>
  <div id="app">
    <h1>Demo_Slider</h1>
    <h1 v-if="loading">Loading...</h1>
    <Slider v-else-if="list.length && !loading" :list="list"></Slider>
  </div>
</template>

<script>
import axios from "axios";
import Slider from "./components/Slider/index";
export default {
  name: "app",
  components: {
    Slider
  },
  data() {
    return {
      list: [],
      loading: false
    };
  },
  async mounted() {
    this.loading = true;
    this.list = await axios.get("slider.json").then(res => res.data.list);
    this.loading = false;
  }
};
</script>

<style>
html {
  color: #34495e;
  background-color: #41b883;
  font-family: "微軟正黑體";
  text-align: center;
}
</style>
