<template>
  <ul>
    <li v-for="todoItem in todoList" :key="todoItem.id">
      <div
        :class="{ doneTodo: todoItem.completed }"
        @click="toggleTodo(todoItem.id)"
      >
        <span class="checkIcon">
          <i class="fa fa-check" aria-hidden="true"></i>
        </span>
        {{ todoItem.todo }}
      </div>
      <span class="removeBtn" type="button" @click="removeTodo(todoItem.id)">
        <i class="fa fa-trash-o" aria-hidden="true"></i>
      </span>
    </li>
  </ul>
</template>

<script lang="ts">
export interface TodoItemType {
  id: number;
  todo: string;
  completed: boolean;
}

export default {
  props: ["todoList"],
  methods: {
    toggleTodo(targetId: number) {
      this.$emit("toggleTodoItem", targetId);
    },
    removeTodo(targetId: number) {
      this.$emit("removeTodoItem", targetId);
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0;
  margin-top: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}
li {
  width: 350px;
  height: 45px;
  line-height: 45px;
  display: flex;
  justify-content: space-between;
  background-color: #fff;
  margin: 7px 0px;
  padding: 0px 7px;
  border-radius: 2px;
  cursor: pointer;
}
.checkIcon {
  margin: 0px 7px;
  color: #42b883;
}
.removeBtn {
  margin-right: 7px;
  color: rgb(214, 94, 94);
  cursor: pointer;
}
.doneTodo {
  text-decoration: line-through;
  color: rgb(130, 130, 130);
}
</style>
