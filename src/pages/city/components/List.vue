<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.$store.state.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item of hotCities" :key="item.id" @click="handleCityClick(item.name)">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
          <div class="item border-bottom" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Bscroll from 'better-scroll'
  export default {
    name: "CityList",
    props: {
      cities: Object,
      hotCities: Array,
      letter: String
    },
    methods: {
      handleCityClick (city) {
        this.$store.dispatch("changeCity",city);
        this.$router.push('/')
      }
    },
    mounted () {
      this.scroll = new Bscroll(this.$refs.wrapper)
    },
    watch: {
      letter () {
        if(this.letter){
          const element = this.$refs[this.letter][0];
          this.scroll.scrollToElement(element)
        }
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .border-topbottom
    &:before
      border-color #ccc
    &:after
      border-color #ccc
  .border-bottom
    &:before
      border-color #ccc
  .list
    position absolute
    top 1.58rem
    left 0
    right 0
    bottom 0
    overflow hidden
    .title
      color $darkLightColor
      padding-left .2rem
      background $bgTitle
      line-height .66rem
    .button-list
      overflow hidden
      padding .1rem .6rem .1rem .1rem
      .button-wrapper
        width 33.33%
        float left
        .button
          padding .1rem 0
          border-radius $boderRadius
          margin .1rem
          text-align center
          border .02rem solid #ccc
    .item-list
      .item
        line-height .66rem
        padding-left .2rem
</style>
