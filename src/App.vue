<template>
  <div style="background:#F5FBFF;">
    <Header />
    <router-view />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from "@/components/Header.vue";

export default {
  components: {
    Header,
  },
};
</script>

<style></style>
