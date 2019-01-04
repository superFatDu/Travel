<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <router-link tag="li" class="item border-bottom" v-for="item of recommand" :key="item.id" :to="'/detail/'+item.id">
        <img :src="item.imgUrl" alt="" class="item-img">
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HomeRecommand",
  props: {
    recommandList: Array
  },
  data () {
    return {
      /*recommandList: [{
        id: '0001',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_150x150_06cb3e52.jpg',
        title: '北京欢乐谷',
        desc: '太阳神车和黄色过山车都可以，爱琴海主题里的项目都开了.'
      },{
        id: '0002',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_150x150_06cb3e52.jpg',
        title: '北京欢乐谷',
        desc: '太阳神车和黄色过山车都可以，爱琴海主题里的项目都开了.'
      },{
        id: '0003',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_150x150_06cb3e52.jpg',
        title: '北京欢乐谷',
        desc: '太阳神车和黄色过山车都可以，爱琴海主题里的项目都开了.'
      },{
        id: '0004',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_150x150_06cb3e52.jpg',
        title: '北京欢乐谷',
        desc: '太阳神车和黄色过山车都可以，爱琴海主题里的项目都开了.'
      },{
        id: '0005',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_150x150_06cb3e52.jpg',
        title: '北京欢乐谷',
        desc: '太阳神车和黄色过山车都可以，爱琴海主题里的项目都开了.'
      },{
        id: '0006',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_150x150_06cb3e52.jpg',
        title: '北京欢乐谷',
        desc: '太阳神车和黄色过山车都可以，爱琴海主题里的项目都开了.'
      },{
        id: '0007',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_150x150_06cb3e52.jpg',
        title: '北京欢乐谷',
        desc: '太阳神车和黄色过山车都可以，爱琴海主题里的项目都开了.'
      }]*/
    }
  },
  computed: {
    recommand () {
      const recommand = [];
      this.recommandList.forEach((item,index)=>{
        if(index <= 4){
          recommand.push(item);
        }
      });
      return recommand;
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
  .item
    overflow hidden
    height 1.9rem
    display flex
    .item-img
      width 1.5rem
      height 1.5rem
      padding .2rem
    .item-info
      flex 1
      padding .1rem
      min-width 0
      .item-title
        line-height .54rem
        font-size .26rem
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
