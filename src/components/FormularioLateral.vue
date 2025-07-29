<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" placeholder="Qual tarefa você deseja iniciar?" class="input" v-model="descricao" />
            </div>
            <BotaoTempo />

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

    methods: {
        finalizacaoTarefa(tempoEmSegundos: number): void {
            console.log("O tempo foi de: ", tempoEmSegundos)
            console.log("Descrição da tarefa: ", this.descricao)
            this.descricao = ''
        }
    }
});
</script>

<!-- Pai passa pro filho via props -->