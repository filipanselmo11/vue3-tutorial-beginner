<template>
  <div class="nova-tarefa-input">
    <h1>Adicionando nova tarefa</h1>
    <span>
      Você tem {{ allTasks }} {{ allTasks > 1 ? "tarefas" : "tarefas" }} no
      momento.
    </span>
    <div class="nova-tarefa-form">
      <input
        type="text"
        v-model="newTask"
        @keyup.enter="addTask"
        placeholder="Add Nova Tarefa" />
      <!-- <button @click="addTask" :disabled="newTask.length < 1">
        Adicionar Tarefa
      </button> -->
    </div>
    <!-- Atribuir um id ou uma class para essa div -->
    <div v-if="newTask.length > 0">
      <h3>Prévia da Nova Tarefa</h3>
      <p>{{ newTask }}</p>
    </div>
  </div>
  <!-- <div id="lista-de-tarefas"></div> -->
  <div class="lista-de-tarefas">
    <ul>
      <li
        v-for="(task, index) in latest"
        :key="task.id"
        @click="finishTask(task)"
        :class="[
            task.finished ? 'strikeout' : '',
            task.postponed ? 'text-gray': '',
            'simple-class'
        ]">
        {{ index + 1 }}. {{ task.name }}
        <!-- <div id="deletar-tarefa-finalizada"></div> -->
        <div class="deletar-tarefa-finalizada" v-if="task.finished">
          <button @click="removeTask(task.id)">Deletar Tarefa</button>
        </div>
        <!-- <div id="editar-tarefa"></div> -->
        <div class="editar-tarefa" v-else-if="task.edit">
          <button>Editar Tarefa</button>
        </div>
        <!-- <div id="sem-botao"></div> -->
        <div class="sem-botao" v-else></div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data: () => ({
    newTask: "",
    tasks: [
      { id: 1, name: "Aprender Vue 3", finished: false },
      { id: 2, name: "Criar um app com Vue 3", finished: false },
      { id: 3, name: "Escrever um artigo sobre Vue", finished: false },
    ],
  }),
  computed: {
    allTasks() {
      return this.tasks.length;
    },
    latest() {
      return [...this.tasks].reverse();
    },
  },
  methods: {
    addTask() {
      if (this.newTask.length < 1) return;
      this.tasks.push({
        id: this.tasks.length + 1,
        name: this.newTask,
        finished: false,
      });
      this.newTask = "";
    },
    finishTask(task){
        task.finished = true;
    },
    removeTask(id) {
        console.log('Task Removida ', id);
    }
  },
};
</script>

<style scoped>
li::marker {
  display: none !important;
  visibility: hidden !important;
}
.strikeout {
    text-decoration: line-through !important;
}
</style>
