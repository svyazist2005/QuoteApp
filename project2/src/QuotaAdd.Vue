<template>
  <div class='component'>
    <textarea @keyup.enter="addNewQuote" cols="50" rows="10" id="textArea">
    </textarea>
    <br>
    <button class="btn btn-success" @click="addNewQuote">Add quote</button>
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
  methods:{
    checkQuotesQuota(){
      if (this.quotes>=10)
      return false
      else {
        return true
      }
    },
    addNewQuote()
    { if (this.checkQuotesQuota()==true)
      {var quote=document.getElementById("textArea").value;
      console.log(quote);
      console.log(quote.length);
      if (quote.length>1 && quote.trim()!='')
      {eventBus.$emit("addQuote",quote);
      document.getElementById("textArea").value='';}
      else {alert("quote is to small")}}
      else {
        alert("clean your quotes")
      }
    },

  },
  created(){
    eventBus.$on("QuoteCounter",(event)=>{
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
  margin:3px;
}
textarea{
  color:black;
  font-size: 20px;
  font-family: monospace;
  border-radius: 5px;
  border: solid #407F7F 1.5px;
  opacity: 0.7;

}
</style>
