<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" placeholder="Qual tarefa você deseja iniciar?" class="input" v-model="descricao" />
            </div>

            <div class="column">
                <TemporizadorComponent @aoFinalizarTarefa="finalizacaoTarefa" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorComponent from './TemporizadorComponent.vue';


export default defineComponent({
    data() {
        return {
            descricao: ''
        }
    },

    name: 'FormularioLateral',
    components: { TemporizadorComponent },
    emits: ['aoSalvarTarefa'],

    methods: {
        finalizacaoTarefa(tempoEmSegundos: number): void {
            this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: tempoEmSegundos,
                descricao: this.descricao,
            })
            this.descricao = ''
        },
    }
});
</script>

<style>
.formulario {
    color: var(--text-primario);
    background-color: var(--bg-primario)
}
</style>

<!-- Pai passa pro filho via props -->