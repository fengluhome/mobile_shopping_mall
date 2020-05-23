<template lang="html">
    <mt-swipe :auto="4000">
      <mt-swipe-item v-for="k in swiperData" :key="k.id">
        <router-link :to="{ name: '详情页'}">
 <!-- style="width:800px;height:400px" -->
          <img :src="k.imgPath" > 
        </router-link>
      </mt-swipe-item>
    </mt-swipe>

</template>

<script>
export default {
  name: '',
  data() {
    return {
     swiperData:[
             {
             id:1,
            imgPath: require('../../assets/images/广告1.jpg')
          },
          {id:2,
            imgPath: require('../../assets/images/广告2.jpg')
          },
          {id:3,
            imgPath: require('../../assets/images/广告3.jpg')
          },
          {id:4,
            imgPath: require('../../assets/images/广告4.jpg')
          }    
         ]
       }
     }
   }

</script>

<style lang="less" scoped>

.mint-swipe {
  width: 100%;
  height:50vw;
  a,img {
    display: block;
    width: 100%;
    height:100%;
  }
}
</style>
