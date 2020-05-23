<template>
  <section class="section2">
    <div class="section2-list">
      <ul>
        <li v-for="k in list" :key="k.id">
          <router-link :to="{name:'详情页'}">
            <img v-lazy="k.imgPath">
          </router-link>
          <h2 class="section2-list-title ac">
            {{k.title}}
          </h2>
          <p class="section2-list-intro">
            {{k.intro}}
          </p>
          <p class="section2-list-price">
            ￥{{k.price}}
          </p>
        </li>
      </ul>
    </div>
    <router-link class="section2-banner" :to="{name:'详情页'}">
      <img v-lazy="banner" style="width:400px;height:100px">
    </router-link>
  </section>
</template>

<script>
import { Lazyload } from 'mint-ui';

export default {
  props: {
     banner: {
      type: String,
      default:  require('../../assets/images/秒杀2.jpg')
    },
    list: {
      type: Array,
      default: function () {
        return [
          {
         'id':'1',
         'title':'红富士苹果',
        'price':'12/斤',
        'intro': '香甜可口',
        'imgPath': require('../../assets/images/苹果.jpg')
          },
            {
         'id':'2',
         'title':'枣子',
        'price':'10/斤',
        'intro': '有很高的食用，药用价值。酸甜可口',
        'imgPath': require('../../assets/images/枣子.jpg')
          },
            {
         'id':'3',
         'title':'水蜜桃',
        'price':'12/斤',
        'intro': '香甜可口',
        'imgPath': require('../../assets/images/桃子.jpg')
          },
            {
         'id':'4',
         'title':'柠檬',
        'price':'20/斤',
        'intro': '香甜可口',
        'imgPath': require('../../assets/images/柠檬.jpg')
          },
            {
         'id':'5',
         'title':'葡萄',
        'price':'12/斤',
        'intro': '香甜可口',
        'imgPath': require('../../assets/images/葡萄.jpg')
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
.section2-list {
  overflow-x: auto;
  width: 100%;
  .pt();
  /*原生滑动*/
  -webkit-overflow-scrolling: touch;
  > ul {
    .bt();
    display: -ms-flex;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    padding: 6vw;
    width: 380%;
    li {
      margin-right: 10vw;
      width: 26vw;
      a,
      img {
        display: block;
        width: 100%;
      }

      h2,
      p {
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
      }
      h2 {
        .fz(font-size, 32);
        padding-top: 3vw;
        color: #333;
      }

      p.section2-list-intro {
        padding-top: 2vw;
        .fz(font-size, 26);
        color: rgb(150, 150, 150);
      }

      p.section2-list-price {
        color: #b4282d;
      }
    }
  }
}

.section2-banner {
  display: block;
  width: 100vw;
  img {
    display: block;
    height: 24vw;
    width: 100%;
  }
}
</style>
