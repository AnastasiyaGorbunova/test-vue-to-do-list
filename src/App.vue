<template>
  <div>
    <ToDoList />
    <MineCalculator />
    <NoteComments />   
    <FetchWithUsers />       
  </div>
</template>

<script>
import ToDoList from './components/ToDoList.vue';
import MineCalculator from './components/MineCalculator.vue';
import NoteComments from './components/NoteComments.vue';
import FetchWithUsers from './components/FetchWithUsers.vue';

export default {
  name: 'App',
  components: {
    ToDoList,
    MineCalculator,
    NoteComments,
    FetchWithUsers
  }
};
</script>

<style>
</style>
