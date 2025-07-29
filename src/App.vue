<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />

    </div>

    <div class="column is-three-quarter">
      <FormularioLateral />
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioLateral from './components/FormularioLateral.vue';

export default defineComponent({
  name: 'App',
  components: { BarraLateral, FormularioLateral }
});

</script>

<style></style>
