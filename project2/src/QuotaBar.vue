<template>
  <div class='component'>

    <nav aria-label="breadcrumb" class="title">
    <ol class="breadcrumb">
      <li class="breadcrumb-item active" aria-current="page"><b>ADD YOUR QUOTES HERE</b> </li>
    </ol>
    </nav>

    <div class="progress" style="width:100%">
      <div class="progress-bar bg-success" :style="{width:quotes/10*100+'%'}" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100">{{quotes}}/10 quotes</div>
    </div>
  </div>
</template>

<script>
import {eventBus} from './main.js'
export default{
  data:function(){
  return{
    quotes:0
  }
},
created(){
eventBus.$on('QuoteCounter',(event)=>{
  this.quotes=event;
})
}
}

</script>

<style scoped>

.component{
  display:flex;
  flex-direction: column;
  align-items: center;
}
.bar{
  display:flex;
  justify-content: center;
  height: 28px;
  width: 200px;
  background-color: green;
  padding:2px;
  border-radius: 28px;
}
.barframe{
  height: 29px;
  width: 450px;
  border:solid grey;
  border-radius: 29px;
}
.title{
  font-size: 30px;
  font-family:monospace;
  margin:3px;
}

</style>
