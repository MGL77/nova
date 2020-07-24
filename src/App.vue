<template>
  <div id="app">
    <Header /> 
    <router-view />
  </div>
</template>

<script>
import Header from "@/components/header.vue";
export default {
  components: {
    Header,
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
