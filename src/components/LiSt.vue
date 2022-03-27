<template>
  <div>
    <span v-show="!usersItem.length&&!isLoading">欢迎使用</span>
    <span v-show="isLoading&&!usersItem.length&&!errMsg">加载中</span>
    <span v-show="errMsg&&!usersItem.length">{{errMsg}}</span>
    <div v-for="item in usersItem" :key="item.id" v-show="usersItem.length">
        <a v-bind:href="item.html_url">
          <img v-bind:src="item.avatar_url" style="width: 50px;height: 50px">
        </a>
      <span>{{item.login}}</span>
    </div>
  </div>
</template>

<script>
import eventBus from "@/eventBus";
export default {
  name: "LiSt",
  data(){
    return {
      usersItem:[],
      isLoading:false,
      errMsg:''
    }
  },
  mounted() {
    eventBus.$on("getUsers",(users)=>{
      this.usersItem = users
    })
    eventBus.$on('changeLoading',(loading)=>{
      this.isLoading = loading
    })
    eventBus.$on("showErr",(err,users)=>{
      this.errMsg = err
      this.usersItem = users
    })
  }
}

</script>

<style scoped>

</style>