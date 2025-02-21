<template>
    <div>
        <h1>Калькулятор</h1>
        <div class="wrap-text">
        <form id="myForm_one">
            <input type="number" name="number_one" placeholder="Введите первое число">
        </form>
        <div class="wrap-littleButton">
            <button class="littleButton" id="myButton_division">/</button> 
            <button class="littleButton" id="myButton_multiplication">х</button> 
            <button class="littleButton" id="myButton_subtraction">-</button>
            <button class="littleButton" id="myButton_addition">+</button> 
        </div>
        <form id="myForm_two">
            <input type="number" name="number_two" placeholder="Введите второе число">
        </form>
                
        <div class="wrap-textResult">
            <button class="littleButton" id="myButton_equals">=</button> 
            <h3 id="outputTextResult">___________</h3>
        </div>             
        </div>       
    </div>
  </template>
  
  <script>
  export default {
    data() {
        return {
            title: "Привет, Vue.js!",
        };
    },
    methods: {    },
  };
  </script>
  
  <style scoped>
  .wrap-text {
    display: flex;
    flex-direction: column;
    gap: 10px;
    
}

.wrap-textResult {
    display: flex;
    gap: 3px;
    align-items: center;
}

.keyboard {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    gap: 3px;
}

.wrap-littleButton {   
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: flex-start;
    align-content: flex-start;
    gap: 3px;
}

.littleButton {
    font-size: 20px;

    width: 30px;
    height: 30px;
    background: #D9D9D9;
    box-shadow: inset 2px 2px 5px 1px rgba(0, 0, 0, 0.25);
    border: none;    
}

#outputTextResult {
    /*border: none; */
}

/*Hover */
.littleButton:hover {
    background-color: #283593;
}

  </style>
  