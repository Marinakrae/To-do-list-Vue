<template class="header"> 
    <div 
        v-for="objeto in todos"
        v-bind:key="objeto.id"
    >
        <!-- essa variável corresponde ao objeto da posição atual do loop-->
        {{ objeto.title}}
    </div>
</template>

<script>
    export default {
        name: 'App',
        data() {
            return {
                
            }
        }
    }
                    
</script>  

<style>
    .header {
        background: #000;
        color: #fff;
    }

</style>