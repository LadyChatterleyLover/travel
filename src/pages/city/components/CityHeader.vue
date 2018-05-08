<template>
    <div class="header">
      城市选择
      <router-link to="/">
      <div><span class="iconfont header-back">&#xe624;</span></div>
      </router-link>
    </div>
</template>

<script>
    export default {
        name: "city-header"
    }
</script>

<style scoped lang="stylus">
@import "../../../assets/styles/varibles.styl"
.header
  position relative
  height $headerHeight
  overflow hidden
  line-height $headerHeight
  text-align center
  color #fff
  background $bgColor
  font-size .4rem
  .header-back
    top 0
    left 0
    position absolute
    width .64rem
    text-align center
    font-size .4rem
    color #fff
</style>
