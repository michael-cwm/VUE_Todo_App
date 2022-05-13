<template>
  <div class="wrapper">
    <ul>
      <li v-for="(item, i) in todoList" :key="i">
        <span :class="[item.done ? 'doneTodo' : 'undoneTodo']">
          {{ item.description }}
        </span>
        <div class="buttonWrapper">
          <button v-if="item.done" @click="toggleDone(item)">undone</button>
          <button v-else @click="toggleDone(item)">done</button>

          <button @click="deleteTodo(item)">remove</button>
        </div>
      </li>
    </ul>
  </div>
  <div class="wrapper">
    <div class="neo">
      {{ neo }}
    </div>
  </div>
</template>

<script lang="ts">
// import AddTodo from "./AddTodo.vue";
// import { TodoModel } from "@/models/TodoModel";
import { ITask } from "../models/ITask";
import { Vue } from "vue-class-component";
import { Prop } from "vue-property-decorator";

export default class TodoContainer extends Vue {
  @Prop() todoList!: ITask[];
  @Prop() neo!: string;

  toggleDone(item: ITask) {
    item.done = !item.done;
  }

  deleteTodo(id: ITask) {
    const index = this.todoList.indexOf(id, 0);
    this.todoList.splice(index, 1);
  }
}
</script>

<style lang="scss">
.wrapper {
  width: 390px;
  display: flex;
  align-items: center;
  justify-content: center;
  // padding: 0px 10px 0px 10px;
  @media only screen and (min-width: 600px) {
    width: 550px;
  }
}

ul {
  width: 100%;
  padding: 0px;
}

li {
  font-size: 11pt;
  height: 100px;
  display: flex;
  align-items: center;
  gap: 20px;
  justify-content: space-between;
  border-bottom: 3px dotted #22b455;
}

.buttonWrapper {
  display: flex;
  align-items: center;
}

.doneTodo {
  text-decoration: line-through;
}

.neo {
  width: 100%;
  display: flex;
  justify-content: flex-end;
  font-size: 9pt;
}
</style>
