<template>
    <div>
    <div class="search">
      <input type="text" placeholder="输入城市名或拼音" class="search-input" v-model="keyword">
    </div>

      <div class="search-content" ref="search" v-show="keyword">
        <ul>
          <li v-for="item of list" class="search-item border-bottom" :key="item.id" @click="handleCity(item.name)">{{item.name}}</li>
          <li class="search-item border-bottom" v-show="hasNoData">没有匹配的数据</li>
        </ul>
      </div>
    </div>
</template>

<script>
    import Bscroll from "better-scroll"
    import {mapState,mapMutations} from "vuex"
    export default {
      name: "search",
      data() {
        return {
          keyword: "",
          list: [],
          timer: null
        }
      },
      props: {
        cities: Object
      },
      computed:{
        hasNoData(){
          return !this.list.length
        }
      },
      watch: {
        keyword() {
          if (this.timer) {
            clearTimeout(this.timer)
          }
          if (!this.keyword){
            this.list = []
            return
          }
          this.timer = setTimeout(() => {
            const reslut = []
            for (let i in this.cities){
              this.cities[i].forEach((value)=>{
                if (value.spell.indexOf(this.keyword)> -1|| value.name.indexOf(this.keyword) > -1){
                  reslut.push(value)
                }
              })
            }
            this.list = reslut
          }, 100)
        }
      },
      mounted (){
        this.scroll = new Bscroll(this.$refs.search)
      },
      methods:{
        handleCity(city){
          this.changeCity(city)
          this.$router.push("/")
        },
        ...mapMutations(["changeCity"])
      },
    }
</script>

<style scoped lang="stylus">
@import "../../../assets/styles/varibles.styl"
.header
  border-bottom none
 .search
   height .72rem
   background $bgColor
   padding 0 .1rem
   margin-top -0.03rem
   .search-input
     box-sizing border-box
     height .62rem
     line-height .62rem
     width 100%
     padding 0 .1rem
     text-align center
     border-radius .06rem
     color #666
 .search-content
     overflow hidden
     position absolute
     top 1.58rem
     left 0
     right 0
     bottom 0
     background #eee
     z-index 1
    .search-item
      line-height .62rem
      padding-left .2rem
      color #666
      background #fff
</style>
