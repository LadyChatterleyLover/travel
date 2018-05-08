<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list :cities="cities" :hot="hotCities" :letter="letter"></city-list>
    <city-alphabet :cities="cities" @change="handleLetter"></city-alphabet>
  </div>
</template>

<script>
  import axios from "axios"
  import CityHeader from "./components/CityHeader"
  import CitySearch from "./components/Search"
  import CityList from "./components/List"
  import CityAlphabet from "./components/Alphabet"
    export default {
      components: {
        CityHeader,
        CitySearch,
        CityList,
        CityAlphabet
      },
      data (){
        return {
          cities:{},
          hotCities:[],
          letter:""
        }
      },
      methods:{
        getCityInfo(){
          axios.get("/api/city.json").then(this.handleGetCityInfoSucc)
        },
        handleGetCityInfoSucc (res){
          res = res.data
          if (res.ret && res.data){
            const data = res.data
            this.cities = data.cities
            this.hotCities = data.hotCities
          }
        },
        handleLetter (letter){
          this.letter = letter
          // console.log(letter)
        }
      },
      mounted(){
        this.getCityInfo()
      }
    }
</script>

<style scoped>

</style>
