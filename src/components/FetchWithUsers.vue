<template>
    <div>
        <h1>Список пользователей (Fetch API)</h1>
        <button @click='fetchListWithUsers'>Получить список пользователей</button>
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
        fetchListWithUsers() {
            this.statusFetch = "Получаем список...";
            console.log(this.statusFetch);
            fetch('https://rickandmortyapi.com/api/character')
                .then(response => {
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
                    console.log("Получили список");
                    for (let i = 0; i < characters.length; i++) {
                        this.list.push({ name: characters[i].name }); //из-за того, что list оборачивается Proxy-обёртку (в прокси-объект), Vue может отслеживать изменения этого объекта (подписка на событие изменение)
                    }
                    console.log(this.list, []);
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
    gap: 10px;
}
</style>