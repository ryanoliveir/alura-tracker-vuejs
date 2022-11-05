<template>
  <main class="columns is-gapless is-multiline">

    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>

    <div class="column is-three-quarter">
      <FormTask/>
      <!-- Lista de tarefas -->
      
    </div>

  </main>




</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormTask from './components/Formulario.vue';


export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormTask
  }
});
</script>

<style>

header{
  padding: 1rem;
  background-color: #0d3b66;
  width: 100%;
  height: 100vh;

}


@media only screen and (max-width: 768px){
  header{
    padding: 2.5rem;
    height: auto;
  }
}



</style>
