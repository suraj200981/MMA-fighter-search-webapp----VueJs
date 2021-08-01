<template>
  <div>
    <div v-for="fighter in fighters" :key="fighter.FighterId">
      <div class="container">
        <div class="cards">
          <h2 style="padding-top: 50px;">
            {{ fighter.FirstName }} {{ fighter.LastName }}
          </h2>

          <div class="content">
            <div class="details">
              <h2>
                Nickname: <i>"{{ fighter.Nickname }}"</i><br /><span
                  >Senior Designer</span
                >
              </h2>
              <ul class="social_icons">
                <li>
                  <a href="#"><i class="fab fa-facebook-f"></i></a>
                </li>
                <li>
                  <a href="#"><i class="fab fa-twitter"></i></a>
                </li>
                <li>
                  <a href="#"><i class="fab fa-linkedin"></i></a>
                </li>
                <li>
                  <a href="#"><i class="fab fa-instagram"></i></a>
                </li>
              </ul>
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
    };
  },
  //loads as soon as componet is mounted to DOM
  mounted() {
    fetch("http://localhost:3000/fighters")
      .then((response) => response.json())
      .then((data) => (this.fighters = data))
      .catch((err) => console.log(err.message));
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@300;400;500&display=swap");

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
  width: 300px;
  height: 400px;
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
  transform: translateY(30px) scale(0.5);
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
  height: 100%;
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
  color: #fff;
  font-size: 1.5em;
  font-weight: 500;
}

.container .cards .content .details h2 span {
  font-size: 0.8em;
  font-weight: 400;
  color: #03a9f4;
}

.social_icons {
  position: relative;
  display: flex;
  margin-top: 5px;
}

.social_icons li {
  list-style: none;
  margin: 4px;
}

.social_icons li a {
  width: 45px;
  height: 45px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #294d69;
  border-radius: 50%;
  font-size: 1.5em;
  color: #fff;
  text-decoration: none;
  transition: 0.5s;
}

.social_icons li a:hover {
  transform: rotate(360deg);
  background: #03a9f4;
}
</style>
