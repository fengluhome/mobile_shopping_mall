<template lang="html">
  <section class="section4">
    <h2 class="section4-title">
      零食小铺
      <i class="icon-right"></i>
    </h2>
    <ul class="section4-list">
      <li v-for="k in list" :key='k.id'>
        <router-link :to="{name:'详情页'}">
          <img v-lazy="k.imgPath" style="width:165px;height:165px">
          <p>{{k.intro}}</p>
        </router-link>
        <h3>{{k.title}}</h3>
        <span>$ {{k.price}}</span>
      </li>

    </ul>
    <router-link :to="{name:'分类页'}" class="section4-banner">
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
      default: require('../../assets/images/banner4.jpg')
    },
    list: {
      type: Array,
      default: function () {
        return [
            {
         'id':'1',
         'title':'番茄味面包酥',
        'price':'10元/包',
        'intro': '好吃就一个字',
        'imgPath': require('../../assets/images/零食1.jpg')
          },
            {
         'id':'2',
         'title':'旺仔QQ糖',
        'price':'5/包',
        'intro': 'Q弹好吃',
        'imgPath': require('../../assets/images/零食2.jpg')
          },
            {
         'id':'3',
         'title':'卤豆干',
        'price':'12/斤',
        'intro': '香辣可口',
        'imgPath': require('../../assets/images/零食3.jpg')
          },
            {
         'id':'4',
         'title':'甘栗仁',
        'price':'20/斤',
        'intro': '好吃',
        'imgPath': require('../../assets/images/甘栗仁.jpg')
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
.section4 {
  width: 100%;
  overflow: hidden;
  .pt();
  .section4-title {
    .bt();
    text-align: center;
    .fz(font-size, 40);
    padding: 4vw 0;
    position: relative;
    background-color: #ffffff;
    i {
      position: absolute;
      right: 6vw;
      top: 50%;
      .fz(font-size, 36);
      .fz(margin-top,-16);
      &::before {
        color: #9f9f9f;
      }
    }
  }

  .section4-list {
    width: 100%;
    display: -ms-flex;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-pack: center;
    -ms-flex-pack: center;
    justify-content: center;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
    overflow: hidden;
    li {
      width: 50%;
      -webkit-box-sizing: border-box;
      box-sizing: border-box;
      padding: 0 3vw;
      > a {
        display: block;
        width: 100%;
        position: relative;
        img {
          display: block;
          width: 100%;
        }
        p {
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
          position: absolute;
          bottom: 0;
          left: 0;
          width: 100%;
          background-color: gold;
          -webkit-box-sizing: border-box;
          box-sizing: border-box;
          padding: 1.2vw 2vw;
        }
      }

      > h3 {
        padding-top: 3vw;
        .fz(font-size,40);
      }
      > span {
        display: inline-block;
        padding-bottom: 3vw;
        color: #b4282d;
      }
    }
  }

  .section4-banner {
    width: 100%;
    display: block;
    img {
      display: block;
      width: 100%;
    }
  }
}
</style>
