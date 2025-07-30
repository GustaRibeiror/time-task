<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroFormulario :tempoEmSegundos="tarefa.duracaoEmSegundos" />
            </div>
            <div class="column">
                <BotaoExcluir @excluirTarefa="excluirTarefa" :id='tarefa.id' />
            </div>
        </div>
    </div>

</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroFormulario from './CronometroFormulario.vue';
import ITarefa from '@/interfaces/ITarefa';
import BotaoExcluir from './BotaoExcluir.vue';

export default defineComponent({
    name: 'TarefaComponent',
    components: { CronometroFormulario, BotaoExcluir },

    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    },

    methods: {
        excluirTarefa() {
            this.$emit('excluirTarefa', this.tarefa.id)
        }
    }
})
</script>

<style scoped>
.box {
    background: #FAF0CA;
}
</style>