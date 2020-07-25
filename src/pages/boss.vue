<template>
  <div>
    <Zhu />
    <router-view />
    <Tabbar />
  </div>
</template>
<script>
import Zhu from "@/components/zhu.vue";
import Tabbar from "@/components/tabbar.vue";
export default {
  components: {
    Tabbar,
    Zhu,
  },
};
</script>
<style lang="less">
</style>