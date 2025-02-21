<template>
  <div id="app">
    <ToDoList />
    <MineCalculator />
  </div>
</template>

<script>
import MineCalculator from './components/MineCalculator.vue';
import ToDoList from './components/ToDoList.vue';

export default {
  name: 'App',
  components: {
    ToDoList,
    MineCalculator
  }
};
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
