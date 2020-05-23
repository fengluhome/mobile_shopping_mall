<template lang="html">
  <div class="wrap">
    <v-header class="header">
      <h1 slot="title">商品分类</h1>
    </v-header>
    <section class="view">
      <v-aside :datas="allData.data"/>
      <router-view 
        :datas="allData.data" 
      />
    </section>
  </div>
</template>

<script>

import Header from '@/common/_header.vue'
import Aside from '@/components/category/aside.vue'
import category from '@/http/mock.js' //模拟数据
export default {
  components: {
    'v-header': Header,
    'v-aside': Aside
  },
  data () {
    return {
      allData: {}
    }
  },
   methods: {
    getList() {
      var vm = this
      this.axios({
        method: 'get',
        url: 'http://localhost:8082/shop/categoryData'
      })
        .then(res => {
          this.allData = res
            console.log(this.allData)
        })
        .catch(response => {
          console.log(response)
        })
    } 
  },
  mounted() {
    this.getList();
  },
  created () {
    // this.$api({
    //   method: 'get',
    //   url: '/category'
    // }).then((res) => {
    //   this.allData = res.data
    //   console.log(this.allData)
    // }).catch((error) => {
    //   console.log(error)
    // })
  }
}
</script>

<style lang="less" scoped>
.wrap {
  width: 100%;
  height: 100%;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-flow: column nowrap;
  flex-flow: column nowrap;

  .view {
    width: 100%;
    height: 100%;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
  }
}
</style>
