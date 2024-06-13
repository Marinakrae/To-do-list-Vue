<template>
   <!-- O v-if renderiza o componente, o v-show só mostra -->
  <TheHeader
    v-if="showHeader"
  />

  <div v-show="showName">
    <!-- Interpolação ({{}})para utilizar variável no Template-->
    Nome: {{name}}  
  </div>  

  <div v-if="accessLevel === 'admin'">Admin</div>
  <div v-else-if="accessLevel === 'marketing'">Marketing</div>
  <div v-else>User</div>

  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TheHeader from './components/TheHeader';

//Esse objeto default que contém os atributos do componente
export default {
  name: 'App',
  components: {
    HelloWorld,
    TheHeader
  },
  data() {
    //esse data é a central de variáveis do componente
    return {
      showHeader: true,
      name: 'Marina',
      showName: false,
      accessLevel: 'admin'  
    }  
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
