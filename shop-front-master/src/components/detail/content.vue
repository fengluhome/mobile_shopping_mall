<template lang="html">
  <section class="content">
          <h2>商品图片详情</h2>
    <div class="img-wrap" v-for="k in content">
      <img :src="k.imgPath">
    </div>
  </section>

</template>

<script>
export default {
    data() {
      return {
          content:[]
      }
      },
   methods: {

 getList() {
      var vm = this
      this.axios({
        method: 'get',
        url: 'http://localhost:8082/shop/productDetail',
        params: {
          id:this.id
        }
      })
        .then(res => {
          this.content = res.data.data
          console.log(res)
        })
        .catch(response => {
          console.log(response)
        })
    } 

  },
  mounted() {
      this.getList()
  },
  created() {
    this.id = this.$route.params.id
    console.log(this.id)
   },
  computed:{
    content(){
      return this.$store.state.detail.productDatas.contentImgSrc
    }
  }
}
</script>

<style lang="less" scoped>
  .content {
    width: 100%;
    margin-top: 10px;
    border-top: 20px solid #F8FCFF;
    .img-wrap {
    height: 120vw;

      img {
        display: block;
        width: 100%;
        height: 100%;
      }
    }
  }
</style>
