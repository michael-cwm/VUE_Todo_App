<template>
  <Header />
  <div class="flexWrapper">
    <AddTodo />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import AddTodo from "./components/AddTodo.vue";
import TodoContainer from "./components/TodoContainer.vue";
import Header from "./components/Header.vue";

@Options({
  components: {
    Header,
    AddTodo,
    TodoContainer,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
#app {
  font-family: monospace, "Courier New", Courier;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #22b455;
}

html {
  background-color: #020204;
}

body {
  margin: 0px;
}

.flexWrapper {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  max-width: 600px;
  margin: 0 auto;
}
</style>
