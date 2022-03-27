<template>
  <div>
    <input type="text" placeholder="请输入用户名" @keyup.enter="searchUsers" v-model="title">
    <button @click="searchUsers">提交</button>
  </div>
</template>

<script>
import axios from "axios";
import eventBus from "@/eventBus";
export default {
  name: "SearCh",
  data(){
    return {
      title:""
    }
  },
  methods:{
    searchUsers(){
      eventBus.$emit('changeLoading',true)
      axios({
        url:`https://api.github.com/search/users?q=${this.title}`,
        method:'GET',
      }).then((res)=>{
        eventBus.$emit("getUsers",res.data.items)
        eventBus.$emit('changeLoading',false)
      },(err)=>{
        eventBus.$emit("showErr",err.message,[])
      })
    }
  }
}
</script>

<style scoped>

</style>