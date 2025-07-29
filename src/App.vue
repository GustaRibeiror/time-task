<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />

    </div>

    <div class="column is-three-quarter">
      <FormularioLateral @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <TarefaComponent v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
      </div>

    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioLateral from './components/FormularioLateral.vue';
import TarefaComponent from './components/TarefaComponent.vue';
import ITarefa from './interfaces/ITarefa';

export default defineComponent({
  name: 'App',
  components: { BarraLateral, FormularioLateral, TarefaComponent },

  //criar uma coisa que salve uma tarefa e adiciona o resultado em uma lista?

  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },

  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    }
  }
});

</script>

<style scoped>
.lista {
  padding: 1.25rem;
}
</style>
