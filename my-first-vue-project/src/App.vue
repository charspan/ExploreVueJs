<template>
  <div id="app">
    <img src="./assets/logo.png">
    <hello></hello>    
  </div>
</template>

<script>
// import 是 es6 的语法
import Hello from './components/Hello'
// 类似 module.export = { }
// export 项目会自动生成 new Vue({})
export default {
  name: 'app',
  components: {
    Hello
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
