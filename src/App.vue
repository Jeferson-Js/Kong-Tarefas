<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
       <Tarefa v-for="(tarefa, index) in tarefas" :key="index"/>
      </div>
    </div>
  </main>
</template>

<script>
import BarraLateral from "./components/BarraLateral.vue";
import Formulario from "./components/Formulario.vue";
import Tarefa from "./components/Tarefa.vue";


export default {
  name: "App",
  components: {
    BarraLateral,
    Formulario,
    Tarefa
},

data () {
  return {
    tarefas: []
  }
},
methods: {
  salvarTarefa(tarefa) {
    this.tarefas.push(tarefa);
  }
},
};
</script>

<style>
.lista {
  padding: 1.25rem;
}

</style>
