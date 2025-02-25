<template>
  <div>
    <ToDoList />
    <MineCalculator />
    <NoteComments />    
  </div>
</template>

<script>
import MineCalculator from './components/MineCalculator.vue';
import ToDoList from './components/ToDoList.vue';
import NoteComments from './components/NoteComments.vue';

export default {
  name: 'App',
  components: {
    ToDoList,
    MineCalculator,
    NoteComments
  }
};
</script>

<style>
</style>
