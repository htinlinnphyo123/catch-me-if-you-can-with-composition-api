<template>
    
    <div v-if="showBlock">
        <div class="block" @click="stopTimer">
            Click Me {{delay}}
        </div>
    </div>


</template>

<script>
import {ref} from 'vue'

export default {
    
    props : ['delay'],
    setup(props,context){

        let showBlock = ref(false);
        let score = ref(0);
        let timeInterval = ref('')

        setTimeout(()=>{
            showBlock.value = true;
            startTimer();
        },props.delay)


        let startTimer = ()=>{
            timeInterval.value = setInterval(()=>{
                score.value += 50;
                console.log(score.value);
            },500)
        }

        let stopTimer = ()=>{
            clearInterval(timeInterval.value);
            context.emit('stopTimer',score.value)            
        }






        return {showBlock,stopTimer}
    }
}
</script>

<style>
.block{
    width:400px;
    height:300px;
    padding:30px 40px;
    border:none;
    background-color:steelblue;
    border-radius:5px;

}
</style>