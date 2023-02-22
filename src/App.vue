<template>

  <button @click="startPlay" :disabled='isPlaying'>Play</button>
  <div v-if="isPlaying">
    <Block :delay='delay' @stopTimer='stopTimer'></Block>
  </div>
  <div v-if="!isPlaying">
    <Result :result='result'></Result>
  </div>

</template>

<script>

import Block from './components/Block.vue';
import {ref} from 'vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components : {Block, Result},

  setup(){

    let isPlaying = ref(false);
    let delay = ref('');
    let result = ref('');

    let startPlay = ()=>{
      isPlaying.value = true;
      delay.value = Math.random()*5000 + 2000;
    }

    let stopTimer = (value)=>{
      isPlaying.value = false;
      result.value = value;
    }



    return {startPlay,isPlaying,delay,stopTimer,result}
  }

}
</script>

<style>
body{
  height:100vh;
  text-align:center;

  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
}
button{
  padding:10px 20px;
  border-radius:5px;
  cursor:pointer;
  border:none;
  background-color:crimson;
  color:#fff;
  margin-bottom:10px;
}
button:disabled{
  background-color:#999;
  cursor:not-allowed;
}
</style>
