<template>
  <div>
    <home-header></home-header>
    <home-swiper :swiperList="swiperList"></home-swiper>
    <home-icons :iconList="iconList"></home-icons>
    <home-recommand :recommandList="recommandList"></home-recommand>
    <home-weekend :weekendList="weekendList"></home-weekend>
  </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommand from './components/Recommand'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import Vuex from 'vuex'
export default{
  name: 'Home',
  data () {
      return {
        swiperList: [],
        iconList: [],
        recommandList: [],
        weekendList: [],
        lastCity: ''
      }
  },
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommand,
    HomeWeekend
  },
  methods: {
    getHomeInfo(){
        axios.get('/api/index.json?city=' + this.$store.state.city).then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc(res){
        res = res.data;
        if(res.ret && res.data){
            const data = res.data;
            this.swiperList = data.swiperList;
            this.iconList = data.iconList;
            this.recommandList = data.recommendList;
            this.weekendList = data.weekendList;
        }
    }
  },
  mounted () {
    this.lastCity = this.$store.state.city;
    this.getHomeInfo();
  },
  activated () {
    if(this.lastCity !== this.$store.state.city){
      this.lastCity = this.$store.state.city;
      this.getHomeInfo();
    }
  }
}
</script>
<style>

</style>
