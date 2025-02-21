<template>
    <div>
      <h1>Задачи</h1>
      <div class="wrap-form">
          <form id="todo_input">
              <input type="text" name="title" placeholder="Впишите название задачи">
          </form> 
          <button id="btnAddElementsList">Добавить задачу</button>
      </div> 
      <ul id="todo_list"></ul>
      <script src="script.js" defer></script>
    </div>
  </template>
  
  <script>
  export default {
    data() {
        let key = "toDoList";
        let listInput = [];
        let keyMark = "mark";
        let listMarked = [];
        const tempList = localStorage.getItem(key);
        const tempMark = localStorage.getItem(keyMark);

        if (tempList && tempMark) {
            const todolist = JSON.parse(tempList);
            const todoMark = JSON.parse(tempMark);
            console.log(todolist);
            console.log(todoMark);

            for (let i = 0; i < todolist.length; i++) {
                listInput[i] = todolist[i];
                listMarked[i] = todoMark[i];
                createAddNewElementList(
                    listInput[i],
                    listInput,
                    listMarked[i],
                    listMarked
                );
            }
        }
    },
    methods: {
        btnAddElementsList() {
            const form = document.getElementById("todo_input");
            const nameInputForm = form.elements["title"];
            if (nameInputForm.value != "") {
                listInput.push(nameInputForm.value);
                listMarked.push("Выполнено");
                localStorage.setItem(key, JSON.stringify(listInput));
                localStorage.setItem(keyMark, JSON.stringify(listMarked));

                createAddNewElementList(
                    nameInputForm.value,
                    listInput,
                    "Выполнено",
                    listMarked
                );

                nameInputForm.value = "";
            }
        },
        


        createAddNewElementList(nameInput, arr, mark, arrMark) {
        let ul = document.getElementById("todo_list");
    
        let li = document.createElement("li");
    
        let name = document.createElement("p");
        let wrapBtn = document.createElement("div");
        let btnRealized = document.createElement("button");
        let btnDelete = document.createElement("button");
    
        li.classList.add("todo-element");
        wrapBtn.classList.add("wrap-btn-element");
        name.textContent = nameInput;
        btnRealized.textContent = mark;
        btnDelete.textContent = "Удалить";
    
        if (btnRealized.textContent === "Выполнено") {
            li.style.background = "white";
        } else if (btnRealized.textContent === "Отметить, как невыполненное") {
            li.style.background = "#81C784";
        }
    
        wrapBtn.appendChild(btnRealized);
        wrapBtn.appendChild(btnDelete);
    
        li.appendChild(name);
        li.appendChild(wrapBtn);
        ul.appendChild(li);
    
        btnRealized.addEventListener("click", function () {
            if (btnRealized.textContent === "Выполнено") {
                li.style.background = "#81C784";
                btnRealized.textContent = "Отметить, как невыполненное";
            } else if (btnRealized.textContent === "Отметить, как невыполненное") {
                li.style.background = "#ffffff";
                btnRealized.textContent = "Выполнено";
            }
    
            for (let i = 0; i < arr.length; i++) {
                if (arr[i] === name.textContent) {
                    arrMark[i] = btnRealized.textContent;
                }
            }
    
            localStorage.setItem(keyMark, JSON.stringify(arrMark));
        });
        btnDelete.addEventListener("click", function () {
            for (let i = 0; i < arr.length; i++) {
                if (arr[i] === name.textContent) {
                    arr.splice(i, 1);
                    localStorage.setItem(key, JSON.stringify(arr));
                }
            }
            ul.removeChild(li);
        });
  }
  
    },
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
  </style>
  