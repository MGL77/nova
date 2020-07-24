<template>
  <div class="header">
    <img src="../assets/Bee_01_01.jpg" alt />
    <div class="cheng">
      <b>lativ</b>
      <p>
        <van-icon name="ellipsis" />
        <van-icon name="stop-circle" />
      </p>
    </div>
    <van-search placeholder="请输入搜索关键词" input-align="center" />
    <ul>
      <li
        @click="UpBottom(index)"
        v-for="(item,index) in list"
        :key="item.id"
        :class="{'active':iNow === index}"
      >{{ item.title }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      list: [],
      iNow: 0,
    };
  },
  methods: {
    UpBottom(index) {
      this.iNow = index;
    },
  },
  async created() {
    let data = await this.axios.get("../../static/json/fenlei.json");
    this.list = data.data.result;
    console.log(this.list);
  },
};
</script>
<style lang="less">
.header {
  .active {
    color: #000;
    border-bottom: 0.02rem solid #000;
  }
  .van-search {
    display: -webkit-box;
    display: -webkit-flex;
    display: flex;
    -webkit-box-align: center;
    -webkit-align-items: center;
    align-items: center;
    box-sizing: border-box;
    padding: 0rem 0.1rem 0rem 0.1rem;
    background-color: #fff;
  }
  ul {
    width: 3.84rem;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    margin: 0.1rem 0rem 0rem 0.1rem;
    li {
      margin-right: 0.26rem;
      height: 0.3rem;
      text-align: center;
      line-height: 0.3rem;
      color: #8b8787;
    }
  }
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