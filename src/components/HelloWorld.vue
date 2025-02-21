<template>
  <div>
      <h1>{{ title }}</h1>
      <button @click="toggleMessage">Показать сообщение</button>
      <p v-if="isMessageVisible">{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
      return {
          title: "Привет, Vue.js!",
          message: "Это ваше первое Vue.js-приложение.",
          isMessageVisible: false,
      };
  },
  methods: {
      toggleMessage() {
          this.isMessageVisible = !this.isMessageVisible;
      },
  },
};
</script>

<style scoped>
h1 {
  color: #42b983;
}
button {
  margin-top: 20px;
}
</style>
