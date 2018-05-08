<template>
  <div class="wrapper">
  <swiper :options="swiperOption" v-if="showSwiper">
    <swiper-slide v-for="item of list" :key="item.id">
      <img :src="item.imgUrl" alt="" class="swiper-img">
    </swiper-slide>
    <div class="swiper-pagination"  slot="pagination"></div>
</swiper>
  </div>
</template>

<script>
    export default {
      props:{
        list:Array
      },
      data() {
        return {
          swiperOption: {
            pagination:".swiper-pagination",
            loop:true
          },
        }
      },
      computed:{
          showSwiper (){
            return this.list.length
          }
      }
    }
</script>

<style scoped lang="stylus">
.wrapper >>> .swiper-pagination-bullet-active
  background: #fff
.wrapper
  width :100%
  height :0
  overflow :hidden
  padding-bottom: 31.25%
  background: #eee
  .swiper-img
    width: 100%
</style>
