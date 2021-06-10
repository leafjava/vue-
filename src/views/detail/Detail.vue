<template>
  <div>
    <detail-nav-bar></detail-nav-bar>
    <detail-swiper :topImage="topImage"></detail-swiper>
    <detail-base-info :goods="goods" :columns="columns" :services="services"></detail-base-info>
  </div>
</template>

<script>
  import DetailNavBar from './childComps/DetailNavBar'
  import DetailSwiper from './childComps/DetailSwiper'
  import {getDetail} from 'network/detail.js'
  import DetailBaseInfo from './childComps/DetailBaseInfo'

  export default {
    name: "detail",
    components:{
      DetailNavBar,
      DetailSwiper,
      DetailBaseInfo
    },
    data() {
      return {
        iid: null,
        detail:null,
        topImage:[],
        goods:{},
        columns:[],
        services:[]
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
        // console.log(this.topImage)
        // console.log(this.columns)
        console.log(this.services);
      })

    }
  }
</script>

<style scoped>

</style>