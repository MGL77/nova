<template>
  <div class="zhu">
    <img src="../assets/Bee_01_01.jpg" alt />
    <div class="cheng">
      <b>lativ</b>
      <p>
        <van-icon name="ellipsis" />
        <van-icon name="stop-circle" />
      </p>
    </div>
    <van-search placeholder="请输入搜索关键词" input-align="center" @click="btn" />
  </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  methods: {
    btn() {
      this.$router.push({
        path: "/ss",
      });
    },
  },
};
</script>
<style lang="less">
.zhu {
  img {
    width: 4rem;
  }
  .cheng {
    width: 3.74rem;
    height: 0.4rem;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 0.04rem 0rem 0.04rem 0.1rem;
    b {
      font-size: 0.18rem;
    }
    p {
      width: 0.8rem;
      height: 0.3rem;
      border-radius: 0.2rem;
      border: 0.01rem solid #f5f5f5;
      display: flex;
      align-items: center;
      justify-content: space-around;
      .van-icon-ellipsis::before {
        content: "\F04E";
        font-size: 0.16rem;
      }
      .van-icon-stop-circle::before {
        content: "\F0C6";
        font-size: 0.16rem;
      }
    }
  }
}
</style>