<template>
  <div id="detail">
    <detail-nav-bar class="detail-nav"></detail-nav-bar>
    <scroll ref="scroll">
      <detail-swiper :topImage="topImage"></detail-swiper>
      <detail-base-info :goods="goods" :columns="columns" :services="services"></detail-base-info>
      <detail-shop-info :shop="shop" @shopLoad="shopLoad"></detail-shop-info>
      <detail-params-info :params="params"></detail-params-info>
    </scroll>
  </div>
</template>

<script>
  import DetailNavBar from './childComps/DetailNavBar'
  import DetailSwiper from './childComps/DetailSwiper'
  import {getDetail,Shop,GoodsParam} from 'network/detail.js'
  import DetailBaseInfo from './childComps/DetailBaseInfo'
  import DetailShopInfo from './childComps/DetailShopInfo'
  import Scroll from 'components/common/scroll/Scroll'
  import DetailParamsInfo from './childComps/DetailParamsInfo'

  export default {
    name: "detail",
    components:{
      DetailNavBar,
      DetailSwiper,
      DetailBaseInfo,
      DetailShopInfo,
      Scroll,
      DetailParamsInfo
    },
    data() {
      return {
        iid: null,
        detail:null,
        topImage:[],
        goods:{},
        columns:[],
        services:[],
        detailInfo:[],
        shop:{},
        params:{}
      }
    },
    created() {
      // this.iid = this.$route.params.iid
      this.iid = this.$route.query.iid
    },
    mounted() {
      getDetail(this.iid).then(res => {
        console.log(res);
        const data = res.result;
        this.topImage = data.itemInfo.topImages
        this.goods = data.itemInfo
        this.columns = data.columns
        this.services = data.shopInfo.services
        this.shop = new Shop(data.shopInfo);
        this.params = new GoodsParam(data.itemParams.info,data.itemParams.rule)
        // console.log(this.topImage)
        // console.log(this.columns)
        // console.log(this.services);
      })
    },
    methods:{
      shopLoad() {
        this.$refs.scroll.refresh()
      }
    }
  }
</script>

<style scoped>
  #detail {
    position:relative;
    z-index:9;
    background-color: #fff;
  }

  .detail-nav {
    position:relative;
    z-index: 9;
    background-color: #fff;
  }
</style>