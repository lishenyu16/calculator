<template>
  <div id="app">
    <h1>A Simple Calculator By Vue.js</h1>
    <calculator-app></calculator-app>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'
export default {
  name: 'app',
  components:{
    'calculatorApp': Calculator
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style scoped>
html,body{
    margin:0;
    box-sizing: border-box;
}
body{
  background-color:#f4f1f1; 
  width:100%;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width:100%;
  background-color: #f5f8f8;
  text-align: center;
}
</style>
