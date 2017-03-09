<template>
  <div id="app">
    <img src="./assets/logo.png">
    <hello></hello>
    <p>clid tells me: {{childWords}}</p>
    <!-- 因为在HTML中，标签的标签名是大小写不敏感的，而在javascript中变量名是大小写敏感的
    要解决这种差异问题，就必须得在两种标准之间做一个转换，所以vuejs的作者就实现了将驼峰法(camelCase)转换到短横线法(kebab-case) -->
    <h4>以下内容来自MyHello</h4>
    <my-hello msgFromHello='msgFromHello:I am your father.'
    v-on:msgFromChild='litenToMyHello'></my-hello>
  </div>
</template>

<script>
// import 是 es6 的语法
import Hello from './components/Hello'
// import Store from './store'
// console.log(Store);
import MyHello from './components/MyHello'
// 类似 module.export = { }
// export 项目会自动生成 new Vue({})
export default {
  name: 'app',
  data (){
    return {
      childWords: 'default msg'
    }
  },
  components: {
    Hello,MyHello//加载自己的组件
  },
  //vue2已经弃用
  // events:{
  //   msgFromChild (msg){
  //     this.childWords=msg;
  //     //console.log(msg);
  //   }
  // },
  methods:{
    litenToMyHello (msg) {
      this.childWords=msg;
      //console.log(msg);
    }
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
  background:;
}
</style>
