<template>
  <main class="columns is-gapless is-multiline modo-escuro">

    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>

    <div class="column is-three-quarter conteudo">
      <FormTask @aoSalvarTarefa="salvarTarefa"/>
      <!-- Lista de tarefas -->
      <div class="lista">
        
       <Tarefa v-for="(tarefa,index) in tarefas" :key="index" :tarefa="tarefa"/> 

       <Box v-if="listaEstaVazia">
         Você não está muito produtivo hoje :(
       </Box>
      </div>
    </div>

  </main>




</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormTask from './components/Formulario.vue';
import Tarefa from './components/Lista.vue'
import ITarefas from './interfaces/ITarefa'
import Box from './components/Box.vue'


export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormTask,
    Tarefa,
    Box
    
  },
  data () {
    return {
      tarefas: [] as ITarefas[]
    }
    
  },
  computed:{
    listaEstaVazia (): boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefas){
      this.tarefas.push(tarefa)
    }

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

.lista{
  padding: 1.25rem;

}

main{
  --bg-primario: #ffffff;
  --texto-primario: #000;
}

main.modo-escuro{
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo{
  background-color: var(--bg-primario);
  
}

</style>
