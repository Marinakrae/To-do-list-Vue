<template>
   <!-- O v-if renderiza o componente, o v-show só mostra -->
  <TheHeader
    v-if="showHeader"
  />

  <div v-show="showName">
    <!-- Interpolação ({{}})para utilizar variável no Template-->
    Nome: {{name}}  
  </div> 
  
  <!--Bind com uma variável que recebe uma classe-->
  <h1 :class="classVar">
    Curso Vue 3
  </h1>
  <!--Ou podemos fazer testes com a classe-->
  <h3 :class="{ 'title': false, 'title-home': isHome}">
    To-do list
  </h3>

  <p :class="['text', {'text-home': isHome}]">
    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptate optio minus eum animi, accusamus tempora reiciendis dolor libero a, consectetur officiis aut nam. Repellendus culpa aperiam, illum ullam at nesciunt!
  </p>

  <!--O v-bind torna o atributo dinâmico, diz que seu valor é uma variável-->
  <!--v-bind: pode ser substituído por : apenas-->
  <div   
      v-for="(obj, index) in todos"
      :key="obj.id"
      class="todos-item"
  >
      <img 
        v-if="obj.imgSrc" 
        v-bind:src="obj.imgSrc"
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
      classVar: 'title',
      isHome: true,
      pClass: 'text',
      todos: [
                    {
                        "userId": 1,
                        "id": 1,
                        "title": "delectus aut autem",
                        "completed": false, 
                        "imgSrc": 'https://via.placeholder.com/15'
                    },
                    {
                        "userId": 1,
                        "id": 2,
                        "title": "quis ut nam facilis et officia qui",
                        "completed": false,
                        "imgSrc": 'https://via.placeholder.com/15'
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
  .title {
    font-size: 30px;
    color: magenta;
  }
  .title-home {
    font-size: 40px;
    color: orange;
  }
  .text {
    color: lightgreen;
  }
  .text-home {
    color: lightskyblue
  }
  .todos-item{
    background: lightpink;
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
