<template>
  <div class='component1'>
        <div class="quotelist" v-for='q in quotes'>
        <quota><div class="quota" @click='deleteQuota($event)'>{{q}}</div></quota>
        </div>
        <nav aria-label="breadcrumb" class="footer">
        <ol class="breadcrumb">
          <li class="breadcrumb-item active" aria-current="page">To delete quote just click on it</li>
        </ol>
        </nav>
  </div>
</template>

<script>
import Quota from 'Quota.vue'
import {eventBus} from './main.js'
export default{
  components:{
    'quota':Quota
  },
props:{quotes:{
  default:["Just a quote", "Another quote with fat fat fat fat fat fat body "]
}},
methods:{
  deleteQuota(event){
    var element=event.currentTarget;
    this.quotes=this.quotes.filter(quote=>quote!=element.innerHTML)
    eventBus.$emit("QuoteCounter",this.quotes.length);
  }
},
created()
{
eventBus.$on('addQuote',(event)=>{
  this.quotes.push(event);
  console.log(this.quotes);
  eventBus.$emit("QuoteCounter",this.quotes.length);
})
eventBus.$emit("QuoteCounter",this.quotes.length);

}

}
</script>

<style scoped>

.quotelist
{
display:inline-flex;
margin:5px;
flex-wrap: wrap;
}

/* .quota
{color:white;
background-color: #AAA639;
width: 150px;
height: auto;
padding:10px;
border-radius: 4px;
border-left:solid 3px #807C15;
cursor:context-menu;
overflow-wrap:break-word;
font-family: 'Dancing Script', cursive;
font-size: 25px;
} */

.footer{
  text-align: center;
  font-size: 20px;
  font-family: monospace;
}

</style>
