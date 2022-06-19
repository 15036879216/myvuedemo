<template>
   <div class='minibox'>
      <h3>{{title}}</h3>
      <!-- <ul>
        <li v-for="(item ,index) in list01" :key="index">{{item}}</li>
      </ul>
      <button @click="change">走一走</button> -->
    </div>
</template>

<script>
export default {
  props:['title'],
  data(){
    
  }
}
</script>

<style scoped>
.minibox{
  width: 500px;
  margin:20px;
  /* height: 400px; */
  border: 2px solid #000;
  border-radius: 15px;
  padding: 15px;
}
</style>