<template>

<div class="start" v-bind:class="{end : currentmodal}">
  <Modal v-on:closeModal="currentmodal = false; clicked=$event" v-bind:onerooms="onerooms" :clicked="clicked" :currentmodal="currentmodal"/>
</div>

<div class="menu">
  <a v-for="(a,i) in menu" :key="i">{{a}}</a>
</div>

<Discount v-if="showDiscount==true"/>

<button v-on:click="priceSort">가격순정렬</button>
<button v-on:click="sortBack">되돌리기</button>

<Card v-on:openModal="currentmodal = true; clicked=$event" v-bind:oneroom="onerooms[i]" v-for="(a,i) in onerooms" :key="a"/>

</template>

<script>
import data from './assets/oneroom.js'
import Discount from './components/Discount.vue'
import Modal from './components/Modal.vue'
import Card from './components/Card.vue'

export default {
  name: 'App',
  data(){
    return{
      showDiscount:true,
      oneroomsOriginal:[...data],
      clicked:0,
      onerooms:data,
      currentmodal:false,
      reportcnt:[0,0,0],
      menu:['home','Shop','About'],
    }
  },
  methods: {
    increase(){
      this.reportcnt++;
    },
    priceSort(){
      this.onerooms.sort(function(a,b){
        return a.price - b.price;
      })
    },
    sortBack(){
      this.onerooms=[...this.oneroomsOriginal];
    }
  },
  mounted() {
    setTimeout(()=>{
      this.showDiscount=false;
    },5000);     
  },
  components: {
    Discount:Discount,
    Modal:Modal,
    Card:Card,
  }
}
</script> 

<style>

.start{
  opacity:0;
  transform:translateX(-1000px);
  transition: all 3s;
}
.end{
  transform: translateX(0);
  opacity: 1;
}
body{
  margin: 0;
}
div{
  box-sizing: border-box;
}

.discount{
  background-color: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

.black-bg{
  width: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.room-img{
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background: white;
  padding: 15px;
  border-radius: 5px;
}

.menu a{
  color: white;
  padding: 10px;
}
</style>
