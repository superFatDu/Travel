<template>
  <div>
    <div class="header">
      城市选择
      <router-link to="/">
        <div class="iconfont back-icon">&#xe624;</div>
      </router-link>
    </div>
    <div class="search">
      <input v-model="keyword" class="search-input" type="text" placeholder="输入城市名或拼音">
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul>
        <li class="search-item border-bottom" v-for="item of list" @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="search-item border-bottom" v-show="hasList">宝宝尽力了，可是什么也没有找到……</li>
      </ul>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
export default {
  name: "CityHeader",
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null/*,
      hasList: false*/
    }
  },
  methods: {
    handleCityClick (city){
      this.$store.dispatch("changeCity",city);
      this.keyword = ''
    }
  },
  watch: {
    keyword(){
      if(this.timer){
        clearTimeout(this.timer);
      }
      if(!this.keyword){
        this.list = [];
        return false;
      }
      this.timer = setTimeout(()=>{
        const result = [];
        for(let i in this.cities){
          this.cities[i].forEach((value)=>{
            if(value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1){
              result.push(value);
            }
          })
        }
        this.list = result;
      },100)
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.search)
  },
  computed: {
    hasList () {
      return  !this.list.length;
    } 
  }
}
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .header
    position relative
    overflow hidden
    height $headerHeight
    line-height $headerHeight
    text-align center
    color #ffffff
    font-size .3rem
    background $bgColor
    .back-icon
      position absolute
      top 0
      left 0
      width .64rem
      text-align center
      color #ffffff
  .search
    overflow hidden
    background $bgColor
    height .72rem
    line-height .66rem
    text-align center
    .search-input
      width 90%
      text-align center
      height .5rem
      margin -.1rem 0 0 0
      border-radius $boderRadius
      color $darkLightColor
      box-sizing border-box
      padding 0 .15rem
  .search-content
    z-index 1
    overflow hidden
    position absolute
    top 1.58rem
    left 0
    right 0
    bottom 0
    background $bgTitle
    .search-item
      line-height .66rem
      padding-left .2rem
      background #fff
</style>
