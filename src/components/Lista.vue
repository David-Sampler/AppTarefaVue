<template>
  <div>
    
    <div v-if="listas.length" class="content">
      
      <Task v-for="(lista,i) in listas" :key="lista.nome" :task="lista" class="task" 
      @taskDelete="$emit('taskDelete',i)" 
      @taskStateChanged="$emit('taskStateChanged',i)"> </Task>
      
    </div>
    <p v-else class="text-base">Você não tem serviços</p>
  </div>
    
</template>

<script>
import Task from "../components/Task.vue";
export default {
  components: { Task },

  props: {
    listas: { type: Array },
  },
};
</script>
  
<style>

.content{
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 15px;
    flex-wrap: wrap;
    margin: 10px;
}
.task{
    margin: 10px;
}
.text-base{
  color: white;
  font-size: 68px;
}
   
</style>