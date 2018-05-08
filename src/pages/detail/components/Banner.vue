<template>
    <div>
    <div class="banner" @click="handleBanner">
      <img class="banner-img" :src="bannerImg" alt="">
    <div class="banner-info">
      <div class="banner-title">{{this.sightName}}</div>
      <div class="banner-num"><span class="iconfont banner-icon">&#xe692;</span>{{this.bannerImgs.length}}</div>
    </div>
    </div>
    <fade-animation>
      <gallary :imgs="bannerImgs" v-show="showGallary" @close="handleBannerClose"></gallary>
   </fade-animation>
    </div>
    
</template>

<script>
    import Gallary from "../../../common/gallary/Gallary"
    import fadeAnimation from "../../../common/fade/FadeAnimation"
    export default {
        name: "banner",
        components:{
          Gallary,
          fadeAnimation
        },
        data(){
          return {
            showGallary:false,
          }
        },
        methods:{
          handleBanner(){
            this.showGallary = true
          },
          handleBannerClose(){
            this.showGallary = false
          }
        },
        props:{
          sightName:String,
          bannerImg:String,
          bannerImgs:Array
        }
    }
</script>

<style scoped>
.banner {
  position:relative;
  overflow:hidden;
  height:0;
  padding-bottom:55%;
}
.banner-img{
  width:100%;
}
.banner-info{
  position:absolute;
  bottom: 0;
  left:0;
  right:0;
  line-height:.6rem;
  display:flex;
  color:#fff;
  background-image:linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,.8));
}
.banner-title{
  flex: 1;
}
.banner-num {
  line-height:.4rem;
  height:.32rem;
  margin-top: .14rem;
  padding:0 .4rem;
  border-radius:.2rem;
  background: rgba(0, 0, 0,.8);
  font-size:.24rem;
}
 .banner-icon{
   font-size:.24rem;
   padding-right: .1rem;
 }
</style>
