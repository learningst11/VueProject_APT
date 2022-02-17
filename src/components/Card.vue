<template>
  <div>
  <img v-bind:src="oneroom.image" class="room-img">
  <h4 v-on:click="send">{{oneroom.title}}</h4>
  <p>{{oneroom.price}}원</p>  
  <!-- <button v-on:click="reportcnt[0]++">허위매물신고</button> <span>신고수 : {{reportcnt[0]}}</span> -->
</div>
</template>

<script>
export default {
    name:'Card',
    props:{
        oneroom:Object,
        clicked:Number,
        currentmodal:Boolean,
    },
    methods:{
      send(){
        this.$emit('openModal', this.oneroom.id)
      }
    }

}
</script>

<style>

</style>