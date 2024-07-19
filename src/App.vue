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

  <!--Classe em variável que pega a classe style-->
  <p :class="pClass">
    Esse texto possui estilização variável. Possui a classe text ou text-home. Como estamos na home, ele é azul claro.
  </p>

  <!--Bind no style, passamos uma variável que possui o style-->
  <p :style="styleClass">
    Esse texto recebe seu estilo por meio de uma variável exportada na seção default desse arquivo. 
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

  <!-- diretiva v-model (two way significa que o sistema e o usuário editam o valor)-->
  <div>
      <div>
          <br>
          Two-way data binding<br>
          v-model -> formulários <br> <br>
      </div>

      <div>
        <label>Nome:</label> <br>
        <input
          v-model="name"
          type="text"
        > <br>
        Nome digitado: {{name}}
      </div>

      <br><br>

      <div>
        <label>Sports:</label> <br>
        <select v-model="sports">
          <option value="padrao">Escolha</option>
          <option value="futebol">Futs</option>
          <option value="skate">SK8</option>
          <option value="padel">Pads</option>
        </select>
        <br> Valor da variável: {{sports}}
      </div>

      <br><br>

      <div>
        <label>Newsletter</label> <br>
        <input
          v-model="newsletter"
          type="radio"
          value="Sim"
        > Sim

        <input
          v-model="newsletter"
          type="radio"
          value="Não"
        > Não <br>
        O usuário quer receber? {{newsletter}}

      </div>

      <br><br>

      <div>
        <label> Contrato </label> <br>
        <input
          v-model="aceiteContrato"
          type="checkbox"
        > <br> Aceita os nossos termos? 

        {{aceiteContrato}}
      </div>

      <br><br>

      <div>
        <label> Cores que você mais gosta: </label> <br>
        <input
          v-model="colors"
          type="checkbox"
          value="Rosa"
        > Rosa

        <input
          v-model="colors"
          type="checkbox"
          value="Roxo"
        > Roxo

        <br>{{colors}}<br><br>
      </div>
  </div>

  <!--Diretiva v-on - Pega os eventos do js-->
  <!--v-on pode ser substituído por @-->
  <div>
    <!--Pega o evento do clique do botão (Click)-->
    <!--Modificador Once faz com que o método seja executado apenas na 1 vez que é clicado-->
    <button @click.once="onClick">
      Clique aqui
    </button> <br><br>

    <div @mouseover="onMouseOver"
         @mouseout="onMouseOut"
    >
      Passe o mouse  
    </div>

    <br><br>

    <form 
        action="https://google.com"
        @submit.prevent="onSubmit"
    >
      <input
        type="text"
        @keyup.enter="onKeyUp"
      >
      <button type="submit">
        Enviar
      </button>
    </form>

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
      styleClass: {'color': 'pink', backgroundColor: 'green'},
      isHome: true,
      pClass: ['text', 'text-home'],
      sports:'padrao',
      newsletter: 'Sim',
      aceiteContrato: false,
      colors: [],
      todos: [
                    {
                        "userId": 1,
                        "id": 1,
                        "title": "Pegar café",
                        "completed": true, 
                        "imgSrc": 'https://via.placeholder.com/15'
                    },
                    {
                        "userId": 1,
                        "id": 2,
                        "title": "Monitorar chamados",
                        "completed": false,
                        "imgSrc": 'https://via.placeholder.com/15'
                    },
                    {
                        "userId": 1,
                        "id": 3,
                        "title": "Analisar kanbans",
                        "completed": false
                    },
                    {
                        "userId": 1,
                        "id": 4,
                        "title": "Corrigir o Portal da Transparência",
                        "completed": true
                    },
                    {
                        "userId": 1,
                        "id": 5,
                        "title": "Aprender Vue",
                        "completed": false
                    }
                ]        
    }  
  },
  methods: {
    onClick($evento) {
      console.log('click', $evento);
    },
    onMouseOver($evento) {
      console.log("mouse over", $evento);
    },
    onMouseOut($evento){
      console.log("mouse out", $evento)
    },
    onSubmit($evento) {
      console.log('submit', $evento);
    },
    onKeyUp($evento){
      console.log('apertou enter', $evento);
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
