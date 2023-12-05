<template>
  <div id="app">
    <h1>TODO LIST</h1>
    <ToDoInput @add-task="addTask" />
    <ul>
      <ToDoItem
        v-for="(item, index) in tasks"
        :key="index"
        :item="item"
        @toggle-completion="toggleCompletion"
        @delete-task="deleteTask"
      />
    </ul>
  </div>
</template>

<script>
import ToDoInput from './components/ToDoInput.vue';
import ToDoItem from './components/ToDoItem.vue';

export default {
  name: 'App',
  components: {
    ToDoInput,
    ToDoItem,
  },
  data() {
    return {
      tasks: JSON.parse(localStorage.getItem('tasks')) || [],
    };
  },
  methods: {
    addTask(task) {
      this.tasks.push({ task, completed: false });
      this.saveTasks();
    },
    toggleCompletion(item) {
      item.completed = !item.completed;
      this.saveTasks();
    },
    deleteTask(item) {
      this.tasks.splice(this.tasks.indexOf(item), 1);
      this.saveTasks();
    },
    saveTasks() {
      localStorage.setItem('tasks', JSON.stringify(this.tasks));
    },
  },
};
</script>
