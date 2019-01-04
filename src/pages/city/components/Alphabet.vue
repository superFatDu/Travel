<template>
  <div>
    <ul class="list">
      <li class="item" v-for="key of letters" :key="key" @click="handleLetter" :ref="key"
          @touchstart.prevent="handleTouchStart" @touchmove="handleTouchMove" @touchend="handleTouchEnd">{{key}}</li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "CityAlphabet",
    props: {
      cities: Object
    },
    data () {
      return {
        touchStatus: false,
        startY: 0,
        timer: null  /*用于防抖*/
      }
    },
    updated () {
      this.startY = this.$refs['A'][0].offsetTop;
    },
    computed: {
      letters () {
        const letters = [];
        for(let key in this.cities){
          letters.push(key)
        }
        return letters;
      }
    },
    methods: {
      handleLetter (e){
        this.$emit('change',e.target.innerHTML)
      },
      handleTouchStart () {
        this.touchStatus = true
      },
      handleTouchMove (e) { /*move的频率是很高的，通过防抖优化代码+++++其实用节流更好*/
        if(this.touchStatus){
          if(this.timer){
            clearTimeout(this.timer);
          }
          this.timer = setTimeout(()=>{
            const touchY = e.touches[0].clientY - 79;
            const index = Math.floor((touchY - this.startY)/17);
            if(index >= 0 && index < this.letters.length){
              this.$emit('change',this.letters[index])
            }
          },16)
        }
      },
      handleTouchEnd () {
        this.touchStatus = false
      }
    }
  }
</script>

<style lang="stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .list
    position absolute
    right 0
    top 1.58rem
    bottom 0
    width .4rem
    display flex
    flex-direction column
    align-items center
    justify-content center
    .item
      line-height .34rem
      color $darkTextColor
</style>
