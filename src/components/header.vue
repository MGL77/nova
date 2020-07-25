<template>
  <div class="header">
    <!-- 分类 -->
    <div class="JJ">
      <ul class="big">
        <li
          @click="UpBottom(index,item._id)"
          v-for="(item,index) in list"
          :key="item.id"
          :class="{'active':iNow === index}"
        >{{ item.title }}</li>
      </ul>
    </div>

    <!-- 排序 -->
    <ul class="sort">
      <li>综合</li>
      <li>销量</li>
      <li>新品</li>
      <li @click="sort1">价格</li>
    </ul>

    <!-- 渲染的数据 -->
    <ul class="boss">
      <li v-for="item in array" :key="item.id">
        <img :src="item.s_pic" alt />
        <b>{{ item.title }}</b>
        <div class="J">
          <p>{{ item.price }}</p>
          <van-icon name="cart" />
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      list: [],
      iNow: 0,
      array: [],
      sorts: true,
    };
  },
  methods: {
    UpBottom(index, id) {
      this.iNow = index;
      this.axios.get("../../static/json/list.json").then((msg) => {
        let a = msg.data.result.filter((item) => {
          return item.cid == id;
        });
        this.array = a;
      });
    },

    sort1() {
      if (this.sorts == true) {
        this.sorts = false;
        this.array.sort((a, b) => {
          return a.price - b.price;
        });
      } else {
        this.sorts = true;
        this.array.sort((a, b) => {
          return b.price - a.price;
        });
      }
    },
    
  },
  async created() {
    let data = await this.axios.get("../../static/json/fenlei.json");
    this.list = data.data.result;
  },
  mounted() {
    this.axios.get("../../static/json/list.json").then((res) => {
      let a = res.data.result;
      this.array = a;
    });
  },
};
</script>
<style lang="less">
.header {
  .sort {
    width: 4rem;
    height: 0.4rem;
    display: flex;
    align-items: center;
    margin-bottom: 0.2rem;
    li {
      margin: 0rem 0.16rem 0rem 0.1rem;
      color: #444444;
    }
  }
  .boss {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-around;
    li {
      width: 1.4rem;
      height: 2.4rem;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      img {
        width: 1.4rem;
        height: 1.6rem;
        border-radius: 0.1rem;
      }
      b {
        width: 1.4rem;
        height: 0.3rem;
        line-height: 0.3rem;
      }
      .J {
        width: 1.4rem;
        display: flex;
        height: 0.3rem;
        align-items: center;
        justify-content: space-between;
        p {
          color: rgb(194, 20, 20);
        }
        .van-icon-cart::before {
          content: "\F027";
          color: #8b8a8a;
        }
      }
    }
  }
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
  .JJ {
    width: 4rem;
    height: 0.4rem;
    overflow: auto;
    .big {
      width: 7rem;
      display: flex;
      height: 0.24rem;
      margin-top: 0.14rem;
      li {
        color: #444444;
        margin: 0rem 0.16rem 0rem 0.1rem;
      }
    }
  }
}
</style>