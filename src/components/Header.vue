<template>
  <div style="background:#F5FBFF; width:100%; height:150px;">
    <div
      style="text-align:center;
      padding-right:10px;
      font-size:40px;
      padding-top:60px;
      "
    >
      <router-link to="/">Home </router-link>
      <router-link to="/fighters">Fighters </router-link>
      <router-link to="/news">News </router-link>
      <router-link to="/contact">Contact</router-link>
    </div>
  </div>
</template>
<style scoped>
a {
  color: black !important;
  text-decoration: none !important;
  font-family: Cartoon Regular;
  padding: 25px 25px 25px 25px;
  font-weight: 600;
}
a:hover {
  color: #53e4ff !important;
  text-decoration: none !important;
}
</style>
