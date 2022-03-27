<template>
  <div>
    <SearCh/>
    <LiSt/>
  </div>
</template>

<script>
// import eventBus from "@/eventBus";
import SearCh from "@/components/SearCh";
import LiSt from "@/components/LiSt";
export default {
  name:'App',
  components:{SearCh,LiSt}
}
</script>