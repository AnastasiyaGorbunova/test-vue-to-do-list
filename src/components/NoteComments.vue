<template>
    <div>
        <h1>Комментарии</h1>
        <div class="wrap-form">
            <form id="input">
                <textarea rows="5" cols="80" placeholder="Впишите комментарий" v-model="title"></textarea>
            </form>
            <button @click='onClickButton'>Добавить комментарий</button>
        </div>
        <div>
            <h5>Комментарии:</h5>
            <ul id="list">
                <li class="element-list" v-for="item in list" :key="item.name">
                    <div class="element-comments">{{ item.name }}</div>
                    <button @click='onClickRemove(item)'>Удалить</button>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
const key = "list";
export default {
    data() {
        const tempList = localStorage.getItem(key);
        const list = tempList ? JSON.parse(tempList) : [];

        return {
            list,
            title: ""
        }
    },
    methods: {
        onClickButton() {
            if (this.title == "") return;
            this.list.push({ name: this.title });
            this.title = "";
            this.saveList();
        },

        onClickRemove(event) {
            const pepe = this.list.findIndex((item) => item.name === event.name);
            if (pepe == -1) return;
            this.list.splice(pepe, 1);
            this.saveList();
        },

        saveList() {
            localStorage.setItem(key, JSON.stringify(this.list));
        }

    }
};
</script>

<style scoped>
.wrap-form {
    display: flex;
    flex-direction: column;
    width: 500px;
    gap: 10px;
}

#input {
    display: flex;
    flex-direction: column;
}

#list {
    list-style-type: none;
    padding: 0;
    margin: 0;
}

.element-list {
    width: 500px;
    display: block;
    padding: 10px;
    border-bottom: 1px solid #9E9E9E;

}

.element-comments {
    word-break: break-all;
}
</style>