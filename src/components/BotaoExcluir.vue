<template>
    <button class="button is-danger is-dark" @click="excluirTarefa">Excluir</button>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BotaoExcluir',
    emits: ['excluirTarefa'],
    props: {
        id: {
            type: Number,
            required: true
        }
    },

    methods: {
        excluirTarefa() {
            this.$emit('excluirTarefa', this.id)
        }
    }
})
</script>
