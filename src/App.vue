<template>
  <div id="app">
    <router-view />
    <topbottom />
  </div>
</template>

<script>
import topbottom from "@/components/TopBottom.vue";
export default {
  components: {
    topbottom,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  list-style: none;
  font-size: 0.12rem;
}
img {
  display: block;
}
</style>
