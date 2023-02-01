<template>
  <div id="app">
    <h1>{{ title }}</h1>
    <to-do-list></to-do-list>
  </div>
</template>

<script>
import ToDoList from "./components/ToDoList.vue";

export default {
  name: "App",
  components: {
    ToDoList,
  },
  data: () => ({
    title: "Tarefas a Fazer App",
  }),
};
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
