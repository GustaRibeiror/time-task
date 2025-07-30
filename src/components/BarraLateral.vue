<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="logo do sistema">
    </h1>
    <button class="button is-warning is-light" @click="alternarTema">
      {{ textoTemas }}
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'BarraLateral',
  emits: ['alternarModo'],

  data() {
    return {
      modoEscuro: false
    }
  },

  computed: {
    textoTemas() {
      if (this.modoEscuro) {
        return 'Desativar modo escuro'
      }
      return 'Ativar modo escuro'
    }
  },

  methods: {
    alternarTema() {
      this.modoEscuro = !this.modoEscuro
      this.$emit('alternarModo', this.modoEscuro)
    }
  }
});
</script>

<style scoped>
header {
  padding: 1.5rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>