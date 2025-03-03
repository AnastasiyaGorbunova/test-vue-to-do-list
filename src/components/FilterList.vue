<template>
    <div>
        <h1>Фильтрация</h1>
        
        <input type="text" name="title" placeholder="Впишите имя" v-model="nameInput">
        <ul id="list">
            <li v-for="item in list" :key="item.name">
            {{ item.name }} ({{ item.birthday}}) - {{ item.statusRegistrations }}
            </li>
        </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
        return {
            nameInput: "",
            firstList: [{name: "АБАИМОВ", birthday:  "01.02.2019", statusRegistrations: false},
            {name: "АБАКУМОВ", birthday:  "02.02.1997", statusRegistrations: true},
            {name: "АБАКШИН", birthday:  "03.02.1994", statusRegistrations: false},
            {name: "АБАЛДУЕВ", birthday:  "04.02.2001", statusRegistrations: true},
            {name: "АБАЛКИН", birthday:  "05.02.2019", statusRegistrations: true},
            {name: "АБАТУРИН", birthday:  "06.02.1994", statusRegistrations: false},
            {name: "АБАТУРОВ", birthday:  "07.02.1994", statusRegistrations: false},
            {name: "АБАШИН", birthday:  "08.02.2019", statusRegistrations: true},
            {name: "АБАШКИН", birthday:  "09.02.1997", statusRegistrations: true},
            {name: "АБАЯНЦЕВ", birthday:  "10.02.2001", statusRegistrations: false},
            {name: "АБОИМОВ", birthday:  "01.02.2019", statusRegistrations: true},
            {name: "АБРАМЕНКО", birthday:  "11.02.2001", statusRegistrations: false},
            {name: "АБРАМКИН", birthday:  "13.02.2019", statusRegistrations: true},
            {name: "АБРАМОВ", birthday:  "14.02.1997", statusRegistrations: false},
            {name: "АБРАМОВИЧ", birthday:  "15.02.2019", statusRegistrations: true},
            {name: "АБРАМЦЕВ", birthday:  "16.02.1994", statusRegistrations: false},
            {name: "АБРАМЧУК", birthday:  "17.02.1997", statusRegistrations: true},
            {name: "АБРАМЫЧЕВ", birthday:  "18.02.2001", statusRegistrations: true},
            {name: "АБРАШИН", birthday:  "19.02.2005", statusRegistrations: false},
            {name: "АБРАШКИН", birthday:  "01.02.2001", statusRegistrations: true},
            {name: "АБРИКОСОВ", birthday:  "01.02.1997", statusRegistrations: true},
            {name: "АБРОСИМОВ", birthday:  "20.02.1994", statusRegistrations: false},
            {name: "АБРОСЬКИН", birthday:  "21.02.2005", statusRegistrations: true}]
                       
        }
    },
    computed: { //для тех, кто основан на реактивных переменных
        list: function() {
            let nameInput = this.nameInput.toLowerCase();
            return this.firstList.filter(function (elem) { //создаёт новый массив, где все true
            
                if(nameInput==="") return true;
                else {
                    const buf = elem.name.toLowerCase();
                    //indexOf возвращает индекс, если нашлось совпадение 
                    return buf.indexOf(nameInput) > -1; //возвращает true, если нашлось совпадение

                }
            })
        } 
    }
  };
  </script>
  
  <style scoped>
  </style>
  