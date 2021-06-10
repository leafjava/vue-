<template>
  <div>
    <div class="title">{{goods.title}}</div>

    <div class="totalPrice">
      <span class="price">{{goods.price}}
        <!-- -{{goods.highPrice}}-->
      </span>
      <span class="lowPrice">￥{{goods.lowPrice}}</span>
      <span class="discount">{{goods.discountDesc}}</span>
    </div>

    <div class="collection">
      <span class="collection-data">{{columns[0]}}</span>
      <span class="collection-data">{{columns[1]}}</span>
      <span class="collection-data">{{columns[2]}}</span>
    </div>


    <div class="service-manage">
      <span class="service-item"  v-for="item in services">
        <img :src="item.icon" alt="">
        <span>{{item.name}}</span>
      </span>
    </div>

  </div>
</template>

<script>
  export default {
    name: "DetailBaseInfo",
    props:{
      goods:{
        type:Object,
        default() {
          return {}
        }
      },
      columns: {
        type: Array,
        default() {
          return {}
        }
      },
      services: {
        type: Array,
        default() {
          return []
        }
      }
    }
  }
</script>

<style scoped>
  .title,.price{
    margin:13px 0 0 10px;
    font-size:20px;
    line-height:20px;
    color:black;
  }

  .totalPrice {
    margin-top:20px;
  }

  .price {
    color:deeppink;
    font-size:27px;
    margin:0 0 0 5px;
  }

  .lowPrice {
    margin-left:5px;
    text-decoration:line-through;
  }

  .discount {
    background-color:deeppink;
    color:white;
    border-radius:25px;
    font-size:15px;
    padding:2px 5px;
    position:relative;
    left:3px;
    bottom:10px;
  }

  .collection {
    display:flex;
    margin:20px 0 0 10px;
    font-size:13px;
  }

  .collection-data {
    flex:1;
    justify-content:space-between;
  }

  .service-manage {
    display:flex;
    justify-content:space-between;
    margin-top:30px;
    color:black;
    font-weight:400;
  }


  .service-manage img {
    width:15px;
  }

  .service-manage span {
    font-size:10px;
  }



</style>