<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <h1 align = "center" color = "primary">TODO APP</h1>
    <TodoList />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TodoList from './components/TodoList.vue'
export default {
  name: 'App',
  components: {
    // HelloWorld,
    TodoList
  }
}
</script>

<style>
#app {
  width: 80%;
  margin: 0 auto;
}
</style>
