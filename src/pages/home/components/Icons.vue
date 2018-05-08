<template>
  <div class="icons">
  <swiper >

   <swiper-slide v-for="(page,index) of pages " :key="index">
    <div class="icon" v-for="item of page" :key="item.id">
      <div class="icon-img">
      <img :src="item.imgUrl" alt="" class="img-content">
      </div>
      <p class="icon-desc">{{item.desc}}</p>
    </div>
    </swiper-slide>

    </swiper>
  </div>
</template>

<script>
  export default  {
    props:{
      list:Array
    },
    data () {
      return {
        swiperOption: {
          autoplay:false
        },
      }
    },
    computed:{
      pages (){
        const pages = []
        this.list.forEach((item,index)=>{
          const page = Math.floor(index / 8)
          if(!pages[page]){
            pages[page] = []
          }
          pages[page].push(item)
        })
        return pages
      }
    },

  }
</script>

<style scoped lang="stylus" type="text/stylus">
@import "../../../assets/styles/varibles.styl"
@import "../../../assets/styles/mixins.styl"
.icons >>> .swiper-container
  height 0
  padding-bottom 50%
.icon
  position:relative
  overflow:hidden
  width :25%
  height 0
  padding-bottom :25%
  float :left
  .icon-img
    position :absolute
    top :0
    left :0
    right :0
    bottom :.44rem
    box-sizing border-box
    padding .1rem
    .img-content
      height :100%
      display block
      margin 0 auto
  .icon-desc
    position absolute
    left 0
    right 0
    bottom 0
    height .44rem
    line-height .44rem
    color  $dackTextColor
    text-align center
    ellipsis()

</style>
