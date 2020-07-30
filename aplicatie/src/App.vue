<template>
  <div id="app">
    <Titlu/>
    <br><br><br>
    <Calculator/>

  </div>
</template>



<script>
import Calculator from './components/Calculator.vue'
import Titlu from './components/Titlu.vue'

export default {
  name: 'App',
  components: {
    Calculator,
    Titlu
  }
}
</script>

<style>
body, html{
  height: 100%;
  background-image:url('https://images.unsplash.com/photo-1517059224940-d4af9eec41b7?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=3534&q=80');
  background-repeat:no-repeat ;
  background-size:cover;
  background-attachment: fixed;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
