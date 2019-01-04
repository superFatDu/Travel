<template>
    <div class="">
      <div class="item" v-for="(item,index) in categoryList" :key="index">
          <div class="item-title border-bottom">
              <span class="item-title-icon"></span>
              {{item.title}}
          </div>
          <div v-if="item.children" class="item-children">
            <detail-list :categoryList="item.children"></detail-list>
          </div>
      </div>
    </div>
</template>
<script>
export default{
  name: 'DetailList',
  props: {
    categoryList: Array
  }
}
</script>
<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .item-title
    line-height .8rem
    padding 0 .2rem
    font-size .24rem
    background $bgTitle
  .item-children
    padding 0 .2rem
    background $bgTitle
</style>
