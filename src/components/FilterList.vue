<template>
    <div>
        <h1>Фильтрация</h1>

        <input type="text" name="title" placeholder="Впишите имя" v-model="nameInput">
        <ul id="list">
            <li v-for="item in list" :key="item.name">
                {{ item.name }} ({{ item.birthday }}) - {{ item.statusRegistrations }}
            </li>
        </ul>
    </div>
</template>

<script>
import { listUsers } from '@/const/list-users';

export default {
    data() {

        return {
            nameInput: "",
            firstList: listUsers,

        }
    },
    computed: { //для тех, кто основан на реактивных переменных. Динамические свойства
        //computed - одни данные рассчитываются на основе других

        list() { //= "list: function () {"
            let nameInput = this.nameInput.toLowerCase().trim(); //trim - убирает пробелы
            if (nameInput === "") {
                return this.firstList;
            }
            return this.firstList.filter(function (elem) { //создаёт новый массив, где все true
                const buf = elem.name.toLowerCase();
                //indexOf возвращает индекс, если нашлось совпадение 
                return buf.indexOf(nameInput) > -1; //возвращает true, если нашлось совпадение
            })
        }
    }
};
</script>

<style scoped></style>