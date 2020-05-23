<template lang="html">
  <div class="main">
    <h2>{{_datas.title}}</h2>
    <ul>
      <li
         v-for="(k,i) in _datas.list"
         :key='i'
      >
        <router-link :to="{path:'/detail/'+k.id}">
          <img v-lazy="k.imgPath" style="width:60px;height:60px"><span>{{k.title}}</span>
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import { Lazyload } from 'mint-ui';
export default {
  props: {
    datas: {
      type: Array,
      default: function () {
        return []
      }
    }
  },
  computed: {
    // 获取当前aside栏选择的是第几个
    tabIndex () {
      return this.$store.state.category.tabIndex
    },
    _datas (){
      const _datas =  {
        list:[],
        title:''
      }
      return this.datas[this.tabIndex] || _datas
    }
  },
  methods: {
    getList() {
      var vm = this
      this.axios({
        method: 'get',
        url: 'http://localhost:8082/shop/category',
        params: {
          category:this.category
        }
      })
        .then(res => {
          this._datas.list = res.data.data
          this._datas.title=this.category
          console.log(res)
          console.log(this._datas.title)
        })
        .catch(response => {
          console.log(response)
        })
    } 
  },
  mounted() {
    this.getList();
  },
  created() {
     this.category = this.$route.params.tab
    console.log(this.category)
  },
}
</script>

<style lang="less" scoped>
.main {
  overflow-y: auto;
  -webkit-overflow-scrolling: touch;
  flex: 9.8;
  height: 100%;
  &::-webkit-scrollbar {
    display: none;
  }
  > h2 {
    font-size: 24px;
    padding: 2vw 4vw;
    color: #333;
    letter-spacing: 2px;
    background-color: rgb(247, 247, 247);
  }
  > ul {
    width: 100%;
    display: -webkit-flex;
    display: -ms-flex;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    background-color: rgb(247, 247, 247);

    li {
      background-color: rgb(247, 247, 247);
      width: 33%;
      text-align: center;
      a {
        color: #666;
        display: block;
        img {
          display: block;
          width: 60%;
          margin: 4vw auto;
        }
        span {
          text-align: center;
        }
      }
    }
  }
}
</style>
