<template>
  <div>
   <home-header ></home-header>
   <home-swiper :list="swiperList"></home-swiper>
   <home-icons :list="iconList"></home-icons>
   <home-recommend :list="recommendList"></home-recommend>
   <home-weekend :list="weekendList"></home-weekend>
  </div>
</template>

<script>
    import axios from "axios"
    import HomeHeader from "./components/HomeHeader"
    import HomeSwiper from "./components/Swiper"
    import HomeIcons from "./components/Icons"
    import HomeRecommend from "./components/Recommend"
    import HomeWeekend from "./components/Weekend"
    import { mapState} from "vuex"
    export default {
        data () {
          return {
            swiperList:[],
            iconList:[],
            recommendList:[],
            weekendList:[],
            lastCity:""
          }
        },
        components:{
          HomeHeader,
          HomeSwiper,
          HomeIcons,
          HomeRecommend,
          HomeWeekend
        },
        computed:{
          ...mapState(["city"])
        },
        methods:{
          getHomeInfo (){
            axios.get("/api/index.json?city" + this.city).then(this.getHomeInfoSucc)
          },
          getHomeInfoSucc (res){
            res = res.data
            //console.log(res)
            if(res.ret && res.data){
              const data = res.data
              this.swiperList = data.swiperList
              this.iconList = data.iconList
              this.recommendList = data.recommendList
              this.weekendList = data.weekendList
            }
          }
        },
        mounted(){
          //获得所有模拟数据
          this.lastCity = this.city
          this.getHomeInfo()
        },
        activated(){
          if (this.lastCity !== this.city){
            this.lastCity = this.city
            this.getHomeInfo()
          }
        }
    }
</script>

<style scoped>

</style>
