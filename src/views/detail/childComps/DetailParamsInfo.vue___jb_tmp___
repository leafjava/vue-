<template>
  <div class="param-info" v-if="Object.keys(params).length !== 0">
    <table v-for="(table, index) in params.sizes"
            class="info-size" :key="index">
      <tr v-for="(item, indey) in table" :key="indey">
        <td v-for="(data, indez) in item" :key="indez">{{data}}</td>
      </tr>
    </table>
    <table class="set-size">
      <tr v-for="(item,index) in params.infos" :key="index">
        <td>{{item.key}}</td>
        <td>{{item.value}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
  export default {
    name: "DetailParamsInfo",
    props: {
      params:{
        type:Object,
        default() {
          return {}
        }
      }
    },
    mounted() {

    }
  }
</script>

<style scoped>
  .param-info {
    padding: 20px 15px;
    font-size: 14px;
    border-bottom: 5px solid #f2f5f8;
  }

  .param-info table {
    /*position:relative;*/
    width: 100%;
    border-collapse: collapse;
    /*border-spacing: 20px 50px;*/
  }

  .param-info table tr {
    height:42px;
  }

  .param-info table tr td {
    border-bottom: 1px solid rgba(100,100,100,0.1)
  }

  .set-size tr td:nth-child(1) {
    width:20vw;
  }

  .set-size tr td:nth-child(2) {
    color:deeppink;
  }
</style>