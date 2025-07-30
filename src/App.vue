<template>
  <main class="columns is-gapless is-multiline " :class="{ 'modo-escuro': tema }">
    <div class="column is-one-quarter">
      <BarraLateral @alternarModo="changeMode" />
    </div>

    <div class="column is-three-quarter conteudo">
      <FormularioLateral @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <TarefaComponent v-for="tarefa in tarefas" :key="tarefa.id" :tarefa="tarefa" @excluirTarefa="removerTarefa" />

        <h1 v-if="tarefas.length === 0" class="subtitle is-4 titulo">
          Ainda não foi adicionada nenhuma tarefa :
        </h1>
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

  data() {
    return {
      tarefas: [] as ITarefa[],
      tema: false
    }
  },

  methods: {
    salvarTarefa(tarefa: ITarefa) {
      tarefa.id = new Date().getTime();
      this.tarefas.push(tarefa)
    },
    removerTarefa(idTarefa: number) {
      let filtro = this.tarefas.filter(item => item.id !== idTarefa);
      this.tarefas = filtro;
    },
    changeMode(modoEscuro: boolean) {
      this.tema = modoEscuro
    }
  }
});

</script>

<style scoped>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --text-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --text-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario)
}

.titulo {
  color: var(--text-primario)
}
</style>
