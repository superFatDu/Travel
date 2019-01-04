<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="item border-bottom" v-for="item of weekendList" :key="item.id">
        <div class="item-img-wrapper">
          <img :src="item.imgUrl" alt="" class="item-img">
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "HomeWeekend",
    props: {
      weekendList: Array
    },
    data () {
      return {
        /*weekendList: [{
          id: '0001',
          imgUrl: 'http://img1.qunarzz.com/sight/source/1603/6d/2f67ae0659f41f.jpg_r_640x214_bf6cbd0b.jpg',
          title: '北京欢乐谷',
          desc: '太阳神车和黄色过山车都可以，爱琴海主题里的项目都开了.'
        },{
          id: '0002',
          imgUrl: 'http://img1.qunarzz.com/sight/source/1505/aa/7baaf8a851d221.jpg_r_640x214_1431200f.jpg',
          title: '北京欢乐谷',
          desc: '太阳神车和黄色过山车都可以，爱琴海主题里的项目都开了.'
        },{
          id: '0003',
          imgUrl: 'http://img1.qunarzz.com/sight/source/1505/ce/bc89bc2f0e33ea.jpg_r_640x214_3e408453.jpg',
          title: '北京欢乐谷',
          desc: '太阳神车和黄色过山车都可以，爱琴海主题里的项目都开了.'
        }]*/
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/mixin.styl"
  @import "~@/assets/styles/varibles.styl"
  .title
    background $bgTitle
    text-indent .2rem
    line-height .8rem
  .item-img-wrapper
    overflow hidden
    height 0
    padding-bottom 37.19%
    .item-img
      width 100%
  .item-info
    flex 1
    padding .25rem 0
    min-width 0
    text-indent .2rem
    .item-title
      line-height .54rem
      font-size .30rem
      font-weight 600
      ellipse()
    .item-desc
      line-height .45rem
      color #666
      ellipse()
    .item-button
      margin-top .1rem
      background #ff9300
      padding .05rem .2rem
      border-radius .06rem
      color #fff

</style>

