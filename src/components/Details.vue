<template>
<div>
    <router-view name="Header"></router-view>
    <router-view name="Details01" :pass-data="obj"></router-view>
    <router-view name="Introduce" :pass-data="obj"></router-view>
    <router-view name="Starman" :pass-data="obj"></router-view>
    <router-view name="Comments" :pass-id="id" :pass-obj="obj"></router-view>
</div>
</template>

<script>
import Vue from 'vue'
import jsonp from 'jsonp'
export default {
  name: 'Details',
  data(){
    return {
      id:"",
      obj:""
    }
  },
  created(){
    this.id = this.$route.params.id;
    //var url = "https://api.douban.com/v2/movie/subject/"+this.id;
    var url = "../../static/20451290.json"
    //console.log(url)
    // jsonp(url,null,(err,data)=>{
    //   if(err){
    //     console.error(err.message);
    //   }else{
    //    console.log(data)
    //    this.obj = data;
    //    //console.log(this.obj)  
    //   }
    // })
    Vue.axios.get(url).then((res)=>{
      //console.log(res.data) 
      return res.data
    }).then((data)=>{
     //console.log(data)
      this.obj = data
    })
  }
}

</script>

<style>

</style>
