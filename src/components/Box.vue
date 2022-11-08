<template>
    <div class="box has-text-weight-bold" :style="estilo">
        <slot></slot>
    </div>


</template>

<script lang="ts">

import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BoxComponent',
    data (){
        return {
            estilo: {
                background: 'bisque',
            // 'background-color': 'bisque'
            // 'backgroundColor': 'bisque'
            }
        }
    }
})

</script>


<!-- <style scoped>

.box{
    background-color: bisque;
}

</style> -->