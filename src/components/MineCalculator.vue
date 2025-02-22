<template>
    <div>
        <h1>Калькулятор</h1>
        <div class="wrap-text">
        <form id="myForm_one">
            <input type="number" name="argumentOne" placeholder="Введите первое число" v-model="argumentOne">
        </form>
        <div class="wrap-littleButton">            
            <button class="littleButton" id="myButton_division" @click ='operator="/"'>/</button> 
            <button class="littleButton" id="myButton_multiplication">х</button> 
            <button class="littleButton" id="myButton_subtraction">-</button>
            <button class="littleButton" id="myButton_addition">+</button> 
        </div>
        <form id="myForm_two">
            <input type="number" name="argumentTwo" placeholder="Введите второе число" v-model="argumentTwo">
        </form>
                
        <div class="wrap-textResult">
            <button class="littleButtonResult" @click ='onClickGettingTheResult'>=</button> 
            <h3 id="outputTextResult">{{ result }}</h3>
        </div>             
        </div>       
    </div>
  </template>
  
  <script>
  export default {
    data() {
        return {
            argumentOne: "",
            argumentTwo: "",
            operator: "",
            result: 0
        };
    },
    methods: {  
        onClickGettingTheResult() {
            if (this.argumentOne == "" || this.argumentTwo == "") {
                this.result = "Введите все числа";
                return;
            }
            if (this.operator === "") {
                this.result = "Выберите оператор";
                return;
            }
            
            switch (this.operator) {
                case '/':
                    this.result = this.argumentOne / this.argumentTwo;
                    break;
                default:                    
                    break;
            }
            this.argumentOne = "";
            this.argumentTwo = "";
        }

      },
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
    
    .littleButton, .littleButtonResult {
        font-size: 20px;

        width: 30px;
        height: 30px;
        background: #D9D9D9;
        box-shadow: inset 2px 2px 5px 1px rgba(0, 0, 0, 0.25);
        border: none;    
    }

    /*Hover */
    .littleButton:hover, .littleButtonResult:hover {
        background-color: #283593;
    }
    
    .littleButton:focus {   
        background: #283593;
    }  

  </style>
  