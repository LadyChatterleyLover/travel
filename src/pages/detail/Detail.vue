<template>
  <div>
    <banner :sightName="sightName" :bannerImg="bannerImg" :bannerImgs="gallaryImgs"></banner>
    <d-header></d-header>
    <div class="content">
      <list :list="list"></list>
    </div>
  </div>
</template>

<script>
    import Banner from "./components/Banner"
    import DHeader from "./components/DHeader"
    import List from "./components/List"
    import axios from "axios"
    export default {
        name: "detail",
        components:{
          Banner,
          DHeader,
          List
        },
        data(){
          return {
            sightName:"",
            bannerImg:"",
            gallaryImgs:[],
            list:[]
          }
        },
        methods:{
          getDetailInfo(){
            axios.get("/api/detail.json",{
              params:{
                id:this.$route.params.id
              }
            }).then(this.handleGetDataSucc)
          },
          handleGetDataSucc(res){
            res = res.data
            if (res.ret && res.data){
              const data = res.data
              this.sightName = data.sightName
              this.bannerImg = data.bannerImg
              this.gallaryImgs = data.gallaryImgs
              this.list = data.categoryList

            }
          }
        },
        mounted(){
          this.getDetailInfo()
        }
    }
</script>

<style scoped>
.content{
  height: 50rem;
}
</style>
