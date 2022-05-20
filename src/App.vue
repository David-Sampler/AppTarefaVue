<template >
  <div class="bg-gray-700 cont">
    <h1 class="font-bold p-6 text-4xl text-white">Tarefas</h1>
    <TaskProgress :progress="progress" />
    <NewTask @Adicionado="addtak" />
    <div>
      <Lista :listas="tasks" @taskDelete="delet" @taskStateChanged="alterar" />
    </div>
  </div>
</template>

<script>
import Lista from "./components/Lista.vue";
import NewTask from "./components/NewTask.vue";
import TaskProgress from "./components/TaskProgress.vue";

export default {
  components: { Lista, NewTask, TaskProgress },

  data() {
    return {
      tasks: [],
    };
  },

  computed: {
    progress() {
      const total = this.tasks.length;
      console.log(total);
      const done = this.tasks.filter((r) => !r.pending).length;
      console.log(done);
      return Math.round((done / total) * 100) || 0;
    },
  },

  watch: {
    tasks: {
      deep: true,
      handler() {
        localStorage.setItem("tasks", JSON.stringify(this.tasks));
      },
    },
  },

  created() {
    const dados = localStorage.getItem("tasks");
    this.tasks = JSON.parse(dados) || [];
    console.log("aqui", dados);
  },
  methods: {
    addtak(task) {
      const sameName = (r) => r.nome === task.nome;
      const reallyNew = this.tasks.filter(sameName).length == 0;

      if (reallyNew) {
        this.tasks.push({
          nome: task.nome,
          pending: task.pending || true,
        });
        //localStorage.setItem("tasks", JSON.stringify(this.tasks));
      } else {
        alert("TAREFA JÁ EXISTI");
      }
    },
    delet(i) {
      console.log(i);
      this.tasks.splice(i, 1);
    },

    alterar(i) {
      this.tasks[i].pending = !this.tasks[i].pending;
    },
  },
};
</script>

<style>
.cont {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
  flex-direction: column;
}
</style>
