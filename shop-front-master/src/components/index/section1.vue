<template lang="html">
  <section class="section1">
    <h1 class="section1-title">
      家居生活
      <i class="icon-right"></i>
    </h1>
    <ul class="section1-list">
      <li v-for="k in list" :key="k.id">
        <router-link :to="{path:'/category/'+k.title}">
          <img v-lazy="k.imgPath" alt="">
          <h2 align="center">{{k.title}}</h2>
        </router-link>
      </li>
    </ul>
  <router-link :to="{ name: '详情页'}"  class="section1-banner">
    <img v-lazy="banner">
  </router-link>
  </section>
</template>

<script>
import { Lazyload } from 'mint-ui';

export default {
  props: {
     banner: {
      type: String,
      default:  require('../../assets/images/banner1.jpg')
    },
    list: {
      type: Array,
      default: function () {
        return [
           {
             id:1,
            imgPath: require('../../assets/images/水果1.jpg'),
            title:'蔬菜'
          },
           {id:4,
            imgPath: require('../../assets/images/水果4.jpg'),
             title:'水果'
          }  
          ,
          {id:2,
            imgPath: require('../../assets/images/水果2.jpg'),
             title:'家电'
          },
          {id:3,
            imgPath: require('../../assets/images/水果3.jpg'),
             title:'零食'
          } 
        ]     
      }
    }
  }
}

</script>

<style lang="less" scoped>
@import "../../assets/fz.less";
@import "../../assets/index/style.css";
.section1 {
  .pt();
  .section1-title {
    .bt();
    background-color: #ffffff;
    text-align: center;
    padding: 4vw 0;
    .fz(font-size, 40);
    color: #333;
    position: relative;

    i {
      position: absolute;
      right: 6vw;
      top: 50%;
      .fz(font-size, 36);
      .fz(margin-top,-16);

      &::before {
        color: rgb(159, 159, 159);
      }
    }
  }

  .section1-list {
    display: -ms-flex;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
    -ms-flex-pack: distribute;
    justify-content: space-around;
    padding: 0 2vw 4vw 2vw;
    li {
      width: 50%;
      padding: 1vw;
      -webkit-box-sizing: border-box;
      box-sizing: border-box;
      a,
      img {
        width: 100%;
        display: block;
      }
    }
  }

  .section1-banner {
    display: block;
    width: 100vw;
    img {
      width: 100%;
      height: 24vw;
    }
  }
}
</style>
