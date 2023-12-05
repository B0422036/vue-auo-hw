<template>
  <li class="todo-item">
    <input
      type="checkbox"
      :checked="item.completed"
      @change="toggleCompletion"
      class="checkbox"
    />
    <span :class="{ completed: item.completed, 'task-text': true }">{{
      item.task
    }}</span>
    <button class="delete-btn" @click="deleteTask">刪除</button>
  </li>
</template>

<script>
export default {
  props: ['item'],
  methods: {
    toggleCompletion() {
      this.$emit('toggle-completion', this.item);
    },
    deleteTask() {
      this.$emit('delete-task', this.item);
    },
  },
};
</script>

<style scoped>
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 10px;
}

.checkbox {
  width: 24px;
  height: 24px;
  cursor: pointer;
}

.task-text,
.completed {
  font-size: 20px;
  line-height: 1.2;
}

.completed {
  text-decoration: line-through;
  color: #999;
  flex-grow: 1;
  margin-right: 10px;
}

.delete-btn {
  white-space: nowrap;
  font-size: 18px;
  background-color: red;
  border: none;
  color: white;
  padding: 5px 15px;
  border-radius: 3px;
  cursor: pointer;
}

.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 10px;
  border-bottom: 1px solid #ccc; /* 新增此行 */
}
</style>
