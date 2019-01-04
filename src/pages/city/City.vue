<template>
  <div>
    <city-header :cities="cities"></city-header>
    <city-list :cities="cities" :hotCities="hotCities" :letter="letter"></city-list>
    <city-alphabet :cities="cities" @change="letterChange"></city-alphabet>
  </div>
</template>

<script>
  import axios from 'axios'
  import CityHeader from './components/Header'
  import CityList from './components/List'
  import CityAlphabet from './components/Alphabet'
  export default {
    name: "City",
    data () {
      return {
        cities: {},
        hotCities: [],
        letter: ''
      }
    },
    components: {
      CityHeader,
      CityList,
      CityAlphabet
    },
    methods: {
      getCityInfo(){
        axios.get('/api/city.json').then(this.getCityInfoSucc);
      },
      getCityInfoSucc(res){
        res = res.data;
        if(res.ret && res.data){
          const data = res.data;
          this.cities = data.cities;
          this.hotCities = data.hotCities;
        }
      },
      letterChange(letter){
        this.letter = letter
      }
    },
    mounted () {
      this.getCityInfo();
    }
  }
</script>

<style lang="stylus" scoped>

</style>
