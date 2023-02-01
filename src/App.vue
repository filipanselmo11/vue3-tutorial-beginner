<template>
  <div id="app">
    <img
      :src="logoUrl"
      :alt="logoCaption"
      width="200"
      height="200"/>
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
    logoUrl:
      "https://images.unsplash.com/photo-1507925921958-8a62f3d1a50d?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1955&q=80",
    logoCaption: "A photo by Kelly Sikkema on Unsplash showing post-it notes",
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
