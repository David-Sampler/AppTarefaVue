<template>
  <div>
    <button
      class="
        p-4
        bg-orange-400
        font-bold
        m-2
        rounded-md
        shadow-xl
        hover:bg-indigo-500
        duration-500
      "
      @click="add"
    >
      Adicionar Tarefa
    </button>
    <input
      type="text"
      v-model="nome"
      class="p-4 border-0 font-semibold"
      @keydown.enter="add"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      nome: "",
    };
  },
  methods: {
    limpar() {
      this.nome = "";
    },

    add() {
      if (this.nome == "") {
        alert("Insira a Tarefa no campo");
      } else {
        this.$emit("Adicionado", { nome: this.nome });
        this.limpar();
      }
    },
  },
};
</script>

<style>
</style>