<!--公共画廊组件-->
<template>
    <div class="container" @click="handleGallaryClick">
      <div class="warpper" >
        <swiper :options="SwiperOptions">
          <swiper-slide v-for="(item,index) in imgs" :key="index">
            <img class="g-img" :src="item" alt="">
          </swiper-slide>
          <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
      </div>
    </div>
</template>

<script>
    export default {
        name: "gallary",
        data(){
          return {
            SwiperOptions:{
              pagination:".swiper-pagination",
              paginationType:"fraction",
              observer:true,
              observeParents:true
            }
          }
        },
        props:{
          imgs:{
            type:Array,
            default(){
              return []
            }
          },
        },
        methods:{
        handleGallaryClick(){
          this.$emit("close")
        }
      }
    }
</script>

<style scoped>
.container{
  position: absolute;
  display: flex;
  flex-direction: column;
  justify-content: center;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background: #000000;
  z-index: 6324;
}
.wrapper{
  width: 100%;
  height: 0;
  padding-bottom: 100%;
}
.swiper-container{
  overflow: inherit;
}
.g-img{
  width: 100%;
}
.swiper-pagination{
  color: #fff;
  bottom:-1rem;
}
</style>
