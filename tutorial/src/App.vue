<template>
  <div id="app">
    <todos v-bind:todos="todos"/>
  </div>
</template>

<script>
import Todos from './components/Todos.vue';
export default {
  name: "App",
  components: {Todos},
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "FIRST TODO",
          completed: false,
        },
        {
          id: 2,
          title: "Second TODO",
          completed: false,
        },
        {
          id: 3,
          title: "Third TODO",
          completed: true,
        },
      ],
    };
  },
};
</script>

<style>
</style>
