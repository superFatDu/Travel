<template>
  <div class="icons clearfix">
    <swiper :options="swiperOptionIcon">
      <swiper-slide v-for="(items,index) of pages" :key="index">
        <div class="icon" v-for="item of items" :key="item.id">
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl" alt="">
          </div>
          <p class="icon-desc">{{item.desc}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: "HomeIcons",
  data () {
    return {
      swiperOptionIcon: {
        autoplay: false
      }
    }
  },
  props: {
    iconList: Array
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item,index)=>{
        const page = Math.floor(index/8)
        if(!pages[page]){
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages;
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .icons >>> .swiper-container
    height 0
    padding-bottom 50%
  .icon
    position relative
    width 25%
    height 0
    float left
    padding-bottom 25%
    overflow hidden
    .icon-img
      box-sizing border-box
      padding .1rem
      position absolute
      right 0
      top 0
      bottom .34rem
      left 0
      .icon-img-content
        display block
        margin 8% auto 0 auto
        height 84%
    .icon-desc
      position absolute
      right 0
      bottom .1rem
      left 0
      text-align center
      color: $darkTextColor
      font-weight 600
      height .34rem
      line-height .34rem
</style>
