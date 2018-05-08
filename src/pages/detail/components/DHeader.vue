<template>
    <div>
      <router-link class="head-abs" tag="div" to="/" v-show="showAbs">
        <span class="iconfont back-icon">&#xe624;</span>
      </router-link>
      <div class="fixed" v-show="!showAbs" :style="opacityStyle">
        <router-link to="/">
          <div><span class="iconfont header-back">&#xe624;</span></div>
        </router-link>
        景点详情
      </div>
    </div>
</template>

<script>
    export default {
        name: "d-header",
        data(){
          return {
            showAbs:true,
            opacityStyle:{
              opacity:0
            }
          }
        },
      methods:{
        handleScroll(){
          const top = document.documentElement.scrollTop
          if (top > 60 ){
            let opacity = top / 140
            opacity = opacity > 1 ? 1:opacity
            this.opacityStyle = {
              opacity
            }
            this.showAbs = false
          }else {
            this.showAbs = true
          }
        }
      },
      activated(){
          window.addEventListener("scroll",this.handleScroll)
      },
      deactivated(){
          window.removeEventListener("scroll",this.handleScroll)
      }
    }
</script>

<style scoped>
.head-abs{
  position: absolute;
  left: .2rem;
  top: .2rem;
  width: .8rem;
  height: .8rem;
  border-radius: .4rem;
  text-align: center;
  line-height: .8rem;
  background: rgba(0,0,0,.8);
}
.back-icon{
  color:#fff;
  font-size: .4rem;
}
.fixed{
  z-index: 2;
  position :fixed;
  top: 0;
  right: 0;
  left: 0;
  height: .86rem;
  line-height:.86rem;
  text-align :center;
  color :#fff;
  background: #00bcd4;
  font-size :.4rem;
}
.header-back{
  top :0;
  left: 0;
  position: absolute;
  width: .64rem;
  text-align: center;
  font-size: .4rem;
  color: #fff;
}
</style>
