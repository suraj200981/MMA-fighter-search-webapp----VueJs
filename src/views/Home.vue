<template>
  <div class="home">
    <center>
      <List />
    </center>
  </div>
</template>

<script>
// @ is an alias to /src
import List from "@/components/List.vue";

export default {
  name: "home",
  components: {
    List,
  },
};
</script>
