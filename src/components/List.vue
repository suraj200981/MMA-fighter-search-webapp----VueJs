<template>
  <div>
    <input
      class="searchBox"
      type="text"
      v-model="search"
      placeholder="Search for a fighter"
    />

    <div
      v-for="fighter in filteredFighters"
      :key="fighter.FighterId"
      style="background:#F5FBFF;"
    >
      <h1
        style="padding-top:20px; padding-bottom:20px; color:black; font-weight: 900; font-size:40px;"
      >
        {{ fighter.FirstName }} {{ fighter.LastName }}
      </h1>
      <div class="container">
        <div class="cards">
          <!-- <h1
            style="padding-top: 100px; color:white; font-weight: 900; font-size:40px;"
          >
            {{ fighter.FirstName }} {{ fighter.LastName }}
          </h1> -->
          <div class="imgBx">
            <img
              src="https://www.cnet.com/a/img/LFVAgdx99d77jWrKGNq_65wCd_8=/1200x675/2021/07/10/fcd2e24a-9022-44ba-8f1e-bbbc96f9376b/gettyimages-1327901739.jpg"
            />
          </div>
          <div class="content">
            <div class="details">
              <h2>
                Fighter Profile
                <br />
                <span
                  >Nickname: <i>"{{ fighter.Nickname }}"</i><br /></span
                ><span>Weight class: {{ fighter.WeightClass }}</span>
                <br /><span>Height: {{ fighter.Height }}</span
                ><br /><span>Weight: {{ fighter.Weight }}</span
                ><br /><span>Reach: {{ fighter.Reach }}</span>
              </h2>
              <br />
              <h2>
                Fighter Record
                <br /><span>Wins: {{ fighter.Wins }}</span> <br /><span
                  >Losses: {{ fighter.Losses }}</span
                >
                <br /><span>Draws: {{ fighter.Draws }}</span> <br /><span
                  >Wins: {{ fighter.Wins }}</span
                >
                <br /><span>No contests: {{ fighter.NoContests }}</span>
              </h2>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";

Vue.use(VueAxios, axios);

export default {
  name: "List",

  data() {
    return {
      contents: null,
      fighters: [],
      search: "",
    };
  },
  //loads as soon as componet is mounted to DOM
  mounted() {
    fetch("http://localhost:3000/fighters")
      .then((response) => response.json())
      .then((data) => (this.fighters = data))
      .catch((err) => console.log(err.message));
  },

  computed: {
    filteredFighters: function() {
      return this.fighters.filter((fighter) => {
        var fighterSearch;
        fighterSearch = this.search[0].toUpperCase() + this.search.substring(1);
        return fighter.FirstName.match(fighterSearch);
      });
    },
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
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Josefin Sans", sans-serif;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.container {
  position: relative;
  width: 1280px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.container .cards {
  position: relative;
  width: 500px;
  height: 800px;
  background: linear-gradient(#2196f3, #2196f3 30%, #1d3548 30%, #1d3548);
  margin: 10px;
  border-radius: 20px;
  overflow: hidden;
}
.container .cards .imgBx {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transition: 0.5s;
  z-index: 100000;
  border-radius: 20px;
  overflow: hidden;
  transform-origin: top;
}

.container .cards:hover .imgBx {
  transform: translateY(10px) scale(0.3);
}

.container .cards .imgBx img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.container .cards .content {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 90%;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  padding-bottom: 30px;
  transform: translateY(100%);
  transition: 0.5s;
}

.container .cards:hover .content {
  transform: translateY(0);
}

.container .cards .content .details {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  text-align: center;
}

.container .cards .content .details h2 {
  color: white;
  font-size: 30px;
  font-weight: 500;
}

.container .cards .content .details h2 span {
  font-size: 0.8em;
  font-weight: 400;
  color: #03a9f4;
}
</style>
