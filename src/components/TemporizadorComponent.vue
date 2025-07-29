<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroFormulario :tempoEmSegundos="tempoEmSegundos" />
        <BotaoTempo @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
        <BotaoTempo @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />


    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import CronometroFormulario from './CronometroFormulario.vue'
import BotaoTempo from './BotaoTempo.vue';

export default defineComponent({
    name: 'TemporizadorComponent',


    components: { CronometroFormulario, BotaoTempo },
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },

    methods: {
        iniciar() {
            this.cronometroRodando = true
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1
            }, 1000)

        },
        finalizar() {
            this.cronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('aoFinalizarTarefa', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    },


    emits: ['iniciar', 'finalizar', 'aoFinalizarTarefa']
})
</script>
