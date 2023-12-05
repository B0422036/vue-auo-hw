<template>
  <div class="input-container">
    <input
      type="text"
      v-model="task"
      @keyup.enter="addTask"
      placeholder="輸入待辦事項..."
      class="todo-input"
    />
    <button class="confirm-btn" @click="addTask">確認</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      task: '',
    };
  },
  methods: {
    addTask() {
      if (this.task.trim()) {
        this.$emit('add-task', this.task.trim());
        this.task = '';
      }
    },
  },
};
</script>

<style scoped>
.input-container {
  display: flex;
}

.todo-input {
  font-size: 20px;
  padding: 5px 10px;
  flex-grow: 1;
}

.confirm-btn {
  background-color: #4caf50;
  color: white;
  font-size: 20px;
  padding: 6px 12px;
  border: none;
  cursor: pointer;
}
</style>
