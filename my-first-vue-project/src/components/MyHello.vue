<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{msgFromHello}}</h1>
    <button v-on:click="onClickMe">click!</button>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'hello from component MyHello'
    }
  },
  props:['msgFromHello'],//props 用于两个组件之间的通讯
  methods: {
    onClickMe () {
      //console.log(this.msgFromHello);
      // 通过这个方法向 Hello 组件传递消息,msgFromChild是自己定义的方法名
      this.$emit('msgFromChild',this.msg);//Hello 通过 v-on监听
      //vue2已经弃用
      //this.$dispatch('msgFromChild',this.msg);//Hello通过events 监听
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  -webkit-column-rule: #42b983;
  -moz-column-rule: #42b983;
  -o-column-rule: #42b983;
  column-rule: #42b983;
}

</style>
