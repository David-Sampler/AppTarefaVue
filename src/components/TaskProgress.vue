<template>
  <div class="progress">
      <span class="progress-value">
          {{progress}}%
      </span>
      <div class="progress-bar" :style="{ width:progress + '%' }">

      </div>
  </div>
</template>

<script>
export default {  
    props:{
        progress:{type:Number,default:0}
    }
      
}
</script>

<style>
  .progress{
      position: relative;
      width: 100vh;
      border: 1px solid white ;
      border-radius: 3px;
      display: flex;
      margin-bottom: 16px;
      flex-direction: column;
      align-items: center;
  }
  .progress-bar{
      position: absolute;
      border-radius: 3px;
      height: 100%;
      background-color: rgb(42, 165, 108);
      align-self: flex-start;
  }
  .progress-value{
      z-index: 1;
      color: wheat;
  }
</style>