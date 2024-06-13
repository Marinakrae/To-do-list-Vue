<template>
   <!-- O v-if renderiza o componente, o v-show só mostra -->
  <TheHeader
    v-if="showHeader"
  />

  <div v-show="showName">
    <!-- Interpolação ({{}})para utilizar variável no Template-->
    Nome: {{name}}  
  </div>  

  <div 
      v-for="(obj, index) in todos"
      v-bind:key="obj.id"
      class="todos-item"
  >
      <!-- essa variável corresponde ao objeto da posição atual do loop-->
      {{index}} - {{ obj.title}}
  </div>

</template>

<script>
import TheHeader from './components/TheHeader';

//Esse objeto default que contém os atributos do componente
export default {
  name: 'App',
  components: {
    TheHeader
  },
  data() {
    //esse data é a central de variáveis do componente
    return {
      showHeader: true,
      name: 'Marina',
      showName: false,
      accessLevel: 'admin',
      todos: [
                    {
                        "userId": 1,
                        "id": 1,
                        "title": "delectus aut autem",
                        "completed": false
                    },
                    {
                        "userId": 1,
                        "id": 2,
                        "title": "quis ut nam facilis et officia qui",
                        "completed": false
                    },
                    {
                        "userId": 1,
                        "id": 3,
                        "title": "fugiat veniam minus",
                        "completed": false
                    },
                    {
                        "userId": 1,
                        "id": 4,
                        "title": "et porro tempora",
                        "completed": true
                    },
                    {
                        "userId": 1,
                        "id": 5,
                        "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
                        "completed": false
                    }
                ]  
    }  
  }
}
</script>

<style>
  .todos-item{
    background: #000;
    margin: 0 0 5px 0;
    padding: 3px 6px;
    color: #fff;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 60px;
}
</style>
