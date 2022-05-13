<template>
  <div class="wrapper">
    <form @submit.prevent="onSubmit">
      <input type="text" v-model="inputField" placeholder="type here..." />
      <button @click="addTodo" class="addBtn">add</button>
    </form>
  </div>
  <TodoContainer :todoList="todoArray" :neo="msg" />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import { TodoModel } from "../models/TodoModel";
import { ITask } from "../models/ITask";
import TodoContainer from "./TodoContainer.vue";

@Options({
  components: { TodoContainer },
})
export default class AddTodo extends Vue {
  inputField = "";
  todoArray: ITask[] = [];
  msg = "Powered by Neo";

  addTodo() {
    const newTodo = new TodoModel(this.inputField, Date.now(), false);

    this.todoArray.push(newTodo);

    this.inputField = "";

    // this.todoArray.forEach((task) => {
    //   console.log(task.description);
    // });
  }
}
</script>

<style lang="scss">
input {
  font-family: monospace, "Courier New", Courier;
  color: #22b455;
  height: 40px;
  width: 90%;
  margin: 0px;
  background-color: #020204;
  border: none;
  border-bottom: 1px solid #22b455;
  padding: 0px;
  outline: none;
}

button {
  height: 41px;
  width: 80px;
  background-color: #020204;
  border: 1px solid #22b455;
  padding: 0px 6px 0px 6px;
  color: #22b455;
  font-family: monospace, "Courier New", Courier;
}

form {
  width: 100%;
  display: flex;
  justify-content: space-between;
  height: 40px;
}

.addBtn {
  font-size: 11pt;
}

input::placeholder {
  font-family: monospace, "Courier New", Courier;
  color: #22b455;
}
</style>
