<template>

  <div class="task" :class="stateClass" @click="$emit('taskStateChanged',task)"  >
      <span class="close" @click="$emit('taskDelete',task)">x</span>
      {{task.nome}}
  </div>
</template>

<script>
export default {
     props:{
         task:{type:Object}
     },
     computed:{
         stateClass(){
             return{
                 pending:this.task.pending,
                 done:!this.task.pending
             }
         }
     }
}
</script>

<style>

.task{
    position: relative;
    box-sizing: border-box;
    width: 350px;
    height: 150px;
    padding: 10px;
    border-radius: 10px;
    font-size: 2rem;
    font-weight: 600;
    cursor: pointer;
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
}

.pending{
    border-left: 12px solid #B73229;
    color: white;
    background-color: #F44336;
}
.done{
     color: antiquewhite;
      border-left: 12px solid #29b794;
      background-color: #23845a;
      text-decoration: line-through;
}

.pending .close{
    background-color: #b15e58;
   
}
.done .close{
     background-color: #619e84;
}
.close{
   
    position: absolute;
    top: 10px;
    right: 10px;
    height: 25px;
    width: 25px;
    font-size: 0.9rem;
    font-weight: 600;
    border-radius: 10px;
    display: flex;
    justify-content: center;
   
}

</style>