<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para crianção de uma nova tarefa">

                <input 
                    type="text" 
                    class="input" 
                    name="tasks" 
                    placeholder="Qual tarefa você deseja iniciar?"
                    v-model="descricao">

            </div>
            <div class="column">
                <Temporizador @aoTemporizadorFinalizado="finalizarTarefa" />
            </div>
        </div>
    </div>

</template>

<script lang="ts">

import { defineComponent } from 'vue';
import Temporizador from './Temporizador.vue'

export default defineComponent({
    name: 'FormTask',
    components: {
        Temporizador
    },
    data(){
    return{
        descricao: ''
    }},
    methods:{
        finalizarTarefa(tempoDecorrido: number): void {
            console.log(tempoDecorrido);
            console.log(this.descricao);
            this.descricao = '';
        }
    }
})


</script>

<style>

</style>