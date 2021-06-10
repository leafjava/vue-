<template>
  <nav-bar>
    <div slot="left" @click="backTop"><img class="top-back-img" src="~assets/img/common/back.svg"></div>
    <div slot="center" class="top-layout">
      <p class="top-text" v-for="(item,index) in navbardata" :class="{col:currentIndex === index}" @click="tabClick(index)">{{item}}</p>
    </div>
  </nav-bar>
</template>

<script>
  import NavBar from 'components/common/navbar/NavBar'

  export default {
    name: "DetailNavBar",
    components:{
      NavBar
    },
    data() {
      return {
        navbardata:['商品','参数','评论','推荐'],
        currentIndex:0
      }
    },
    methods:{
      tabClick(index) {
        this.currentIndex = index
      },
      backTop() {
        this.$router.back()
      }
    }
  }
</script>

<style scoped>
  .top-back-img {
    margin-top:9px;
  }

  .top-layout {
    display:flex;
    width:200px;
    margin:auto;
  }

  .top-text {
    flex:1;
    font-size:17px;
  }

  .col {
    color:pink;
  }

</style>