<template>
  <div class="hello">
    <!-- {{}} 是 v-text=""的一个简写方式 -->
    <h1>{{ msg }}</h1>
    <!-- v-bind:class 简写:class="[XXX]" 也能取值-->
    <p :class="[pClass]">{{pClass}}</p>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
      <!-- v-for 用法 -->
      <li v-for="item in items" v-bind:class="{finished: item.isFinished}" v-on:click="toggleFinish(item)">
        {{item.label}}
      </li>
    </ul>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://gitter.im/vuejs/vue" target="_blank">Gitter Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
      <br>
      <li><a href="http://vuejs-templates.github.io/webpack/" target="_blank">Docs for This Template</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
import Store from '../store'
export default {
  name: 'hello',
// function data(){
//   return  {
//       msg: 'Welcome to Your Vue.js App'
//     }
// }
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      // 返回一个数组
      items: [
        // {
        //   label: 'coding',
        //   isFinished: false
        // },
        // {
        //   label: 'walking',
        //   isFinished: true
        // }
      ],
      pClass: 'myP',
      newItem: ''
    }
  },
  watch: {
    msg: {},
    items: {
       handler: function(val,oldVal){
        Store.save(val);
        console.log(Store);
      },
      deep:true //深层复制
    }
    // items: {
    //     // handler: function(val,oldVal){
    //     //     console.log(JSON.stringify(val)+"  "+JSON.stringify(oldVal));
    //     // }
    //   handler: function(val,oldVal){
    //     Store.save(val);
    //     console.log(Store);
    //   },
    //   deep:true //深层复制
    // }
  },
  // 方法一定要写在这里
  methods:{
    toggleFinish: function(item){
      item.isFinished=!item.isFinished;
      //console.log(item);
    },
    addNew: function(){
      //console.log(this.newItem);
      this.items.push({
        label: this.newItem,
        isFinished: false
      });
      this.newItem='';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.myP{
  text-decoration: underline;
}

.finished{
  text-decoration: underline;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
