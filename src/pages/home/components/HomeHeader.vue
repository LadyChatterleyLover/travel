<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont back-icon">&#xe624;</span>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩主题</div>

    <router-link to="/city">
    <div class="header-right">
      {{this.city}}
      <span class="iconfont arrow-icon">&#xe64a;</span>
    </div>
    </router-link>
  </div>
</template>

<script>
    import {mapState} from "vuex"
    export default {
    computed:{
      ...mapState(["city"])
    }
    }
</script>

<style scoped lang="stylus">
  @import "../../../assets/styles/varibles.styl"
.header
    display:flex
    line-height:.86rem
    background:$bgColor
    color:#fff
  .header-left
      width:.64rem
      float:left
   .back-icon
        text-align :center
        font-size :.4rem
        margin-left :.2rem
  .header-right
      min-width:1.04rem
      padding .1rem
      float:right
      text-align:center
      color #fff
    .arrow-icon
      margin-left :-.04rem
      font-size :.24rem
  .header-input
      flex:1
      height :.64rem
      line-height :.64rem
      background :#fff
      border-radius :.1rem
      margin-top :.12rem
      margin-left :.12rem
      color :#ccc
      padding-left :.2rem
</style>
