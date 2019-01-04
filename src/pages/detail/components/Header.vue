<template>
  <div class="header">
    <router-link tag="div" to="/" class="header-abs" v-show="show">
        <span class="iconfont">&#xe624;</span>
    </router-link>
    <div class="header-fixed" v-show="!show" :style="opacityStyle">
      <div class="header-fixed-content">
        景点详情
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      show: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop;
      if(top > 60){
        let opacity = top / 140;
        opacity = opacity > 1 ? 1 : opacity;
        this.opacityStyle = {
          opacity
        }
        this.show = false
      }else{
        this.show = true
      }
    }
  },
  activated () {
    window.addEventListener("scroll", this.handleScroll)
  },
  deactivated () {
    window.removeEventListener("scroll", this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped="">
@import "~@/assets/styles/varibles.styl"
  .header
    .header-abs
      display flex 
      justify-content center
      align-items center
      position absolute
      top .2rem
      left .2rem
      width .8rem 
      height .8rem
      border-radius 50%
      background rgba(0,0,0,.8)
      color #fff
    .header-fixed-content
      position fixed
      top 0
      left 0
      /*overflow hidden*/
      width 100%
      height $headerHeight
      line-height $headerHeight
      text-align center
      color #ffffff
      font-size .3rem
      background $bgColor
      z-index 2
      .header-fixed-back
        position absolute
        top 0
        left 0
        width .64rem
        text-align center
        color #ffffff
      
</style>