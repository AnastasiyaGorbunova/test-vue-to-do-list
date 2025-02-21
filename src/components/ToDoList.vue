<template>
    <div>
      <h1>Задачи</h1>
      <div class="wrap-form">
          <form id="todo_input">
              <input type="text" name="title" placeholder="Впишите название задачи" v-model="title">
          </form> 
          <button @click = 'onClickButton'>Добавить задачу</button>
      </div> 
        <ul id="todo_list">
            <li :class="{ active: item.status }" v-for="item in list" :key="item.name">
            {{ item.name }} <button @click ='onClickChangeStatus(item)'>{{ item.status?"Отметить, как невыполненное":"Выполнено" }}</button>
            <button @click ='onClickRemove(item)'>Удалить</button>
            </li>
        </ul>
    </div>
  </template>
  
  <script>
  const key = "todolist";
  export default {
    data() {
        const tempList = localStorage.getItem(key);
        const list = tempList? JSON.parse(tempList): [];

        return {
            list,
            title: ""
        }
    },
    methods: {
        onClickButton () {
            if (this.title == "") return;
            this.list.push({name: this.title, status: false});
            this.title = "";
            this.saveToDoList();
        },
        onClickChangeStatus (event) {
            event.status = !event.status;
            this.saveToDoList();
        },
        onClickRemove (event) {
            const pepe = this.list.findIndex((item)=>item.name === event.name);
            if (pepe == -1) return; 
            this.list.splice(pepe, 1);
            this.saveToDoList();
        },

        saveToDoList () {
            localStorage.setItem(key, JSON.stringify(this.list));
        }
       
    }    
  };
  </script>
  
  <style scoped>
    .wrap-form {
        display: flex;
        gap:10px;
    }

    .todo-element{
        display: flex;
        height: 30px;
        align-items: center;
        justify-content: space-between;
    }

    .wrap-btn-element {
        display: flex;
        gap: 5px;
    }

    .active {
        background: #81C784;
    }

  </style>
  