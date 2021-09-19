<template>
  <div>
    <input
      class="searchBox"
      type="text"
      v-model="search"
      placeholder="Search for a fighter..."
    />

    <div v-bind="article in news">
      <h1
        style="padding-top:20px; padding-bottom:20px; color:black; font-weight: 900; font-size:40px;"
      >
        {{ article.images.name }}
      </h1>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";

Vue.use(VueAxios, axios);

export default {
  name: "News",

  data() {
    return {
      contents: null,
      news: [],
      search: "",
    };
  },
  //loads as soon as componet is mounted to DOM
  mounted() {
    fetch("http://site.api.espn.com/apis/site/v2/sports/mma/ufc/news", {
      method: "GET",
    })
      .then((response) => {
        console.log(response.json());
      })
      .then((data) => (this.news = data))
      .catch((err) => console.log(err.message));
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@300;400;500&display=swap");

.searchBox {
  width: 50%;
  height: 60%;
  line-height: 30px;
  margin-top: 30px;
  font-size: 24px;
}
</style>
