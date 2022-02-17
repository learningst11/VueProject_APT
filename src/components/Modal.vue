<template>
  <div class="black-bg" v-if="currentmodal==true">
  <div class="white-bg">
    <h4>{{onerooms[clicked].title}}</h4>
    <p>{{onerooms[clicked].content}}</p>
    <input v-model="month">
    <p>{{onerooms[clicked].price*month}}원</p>
    <button v-on:click="$emit('closeModal')">닫기</button>
  </div>
</div>
</template>

<script>
export default {
  name:'Modal',
    data(){
          return{
            month:1,
          }
      },
    props:{
        onerooms:Array,
        clicked:Number,
        currentmodal:Boolean,
    },
  watch:{
    month(a){
      if(a>13){alert("12개월 이하 입력가능");}
      if(isNaN(a)==true){alert("숫자만 입력 가능");
      this.month=1;
      }
    },

  }
}
</script>

<style>

</style>