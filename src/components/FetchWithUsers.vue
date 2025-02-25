<template>
    <div>
        <h1>Список пользователей (Fetch API)</h1>
        <button @click ='fetchListWithUsers'>Получить список пользователей</button>
        <div>{{ statusFetch }}</div>

        <ul id="todo_list">
            <li v-for="item in list" :key="item.name">
            {{ item.name }}
            </li>
        </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {

        return {
            list: [],
            statusFetch: ""
        }
    },
    
    methods: {        
        fetchListWithUsers () {
            fetch('https://rickandmortyapi.com/api/character')
                .then(response => {
                    this.statusFetch = "Получаем список...";
                    if (!response.ok) { 
                        throw new Error('Сетевая ошибка'); 
                    }
                    return response.json(); 
                })
                .then(data => {                    
                    return data.results;
                })
                .then(characters => {
                    this.statusFetch = "Список пользователей:";
                    for (let i = 0; i < characters.length; i++) {
                        this.list.push({name: characters[i].name});
                    }
                })
                .catch(error => {
                    console.error('Ошибка при получении списка пользователей:', error);
                    this.statusFetch = 'Ошибка при получении списка пользователей.';
                });
        }
    }    
  };
  </script>
  
  <style scoped>
    .wrap-form {
        display: flex;
        gap:10px;
    }
  </style>
  