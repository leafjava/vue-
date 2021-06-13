<template>
  <div class="shop">
    <div class="shop-title">
      <div class="shop-title-img">
        <img :src="shop.logo" alt="" class="shop-title-logo"  @load="shopLoad">
      </div>
      <span class="shop-name">{{shop.name}}</span>
    </div>
    <div class="shop-content">
      <div class="shop-content-left">
        <div class="content-left">
          <span>{{sells}}万</span>
          <br/>
          <span>总销量</span>
        </div>
        <div class="content-left">
          <span>{{shop.fans}}</span>
          <br/>
          <span>全部宝贝</span>
        </div>
      </div>
      <div class="center-decoration"></div>
      <div class="shop-content-right">
        <table>
          <tr v-for="item in shop.score">
            <td>{{item.name}}</td>
            <td>{{item.score}}</td>
            <td><p>{{totalScore(item.isBetter)}}</p></td>
          </tr>
        </table>
      </div>
    </div>
    <span class="shop-bottom">进店逛逛</span>
  </div>
</template>

<script>
  export default {
    name: "DetailShopInfo",
    props:{
      detailInfo:{
        type:Array,
        default() {
          return []
        }
      },
      shop:{
        type:Object,
        default() {
          return {}
        }
      }
    },
    mounted() {
    },
    methods:{
      totalScore(data) {
        return data ? '高' : '低'
      },
      shopLoad() {
        this.$emit('shopLoad')
      }
    },
    computed:{
      sells() {
        return parseFloat(this.shop.sells/10000).toFixed(2)
      }
    }
  }
</script>

<style scoped>
  .shop {
    margin:40px 0;
  }

  .shop-title {
    margin:20px 0;
  }

  .shop-title-img {
    position:relative;
    left:10px;
    width:40px;
    height:40px;
    border-radius:20px;
    overflow:hidden;
    background-color: pink;
    box-shadow:0px 0px 2px rgba(0, 0, 0, 0.97)
  }

  .shop-title-logo {
    width:40px;

  }

  .shop-name {
    position:relative;
    left: 60px;
    bottom: 28px;
  }

  .shop-content {
    display:flex;
  }

  [class^="shop-content-"] {
    flex:1;
    color:black;
  }

  .shop-content-left {
    display:flex;
  }

  .content-left {
    flex:1;
    text-align:center;
    font-size:15px;
    font-weight:500;
    color:black;
  }

  .content-left>span:first-child {
    font-size:20px;
  }

  .center-decoration {
    width:1px;
    height:40px;
    background-color: rgba(0, 0, 0, 0.19);
  }

  .shop-content-right table {
    position:relative;
    left:15px;
    border-spacing:8px 8px;
    font-size:12px;
  }

  .shop-content-right tr>td:nth-child(2) {
    color:red;
  }

  .shop-content-right table p {
    background-color:red;
    color:white;
  }

  .shop-bottom {
    display:inline-block;
    position:relative;
    left:50%;
    top:20px;
    transform:translate(-50%,0);
  }
</style>