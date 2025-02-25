<template>
    <div>
        <h1>Калькулятор</h1>
        <div class="wrap-text">
        <form id="myForm_one">
            <input type="number" name="argumentOne" placeholder="Введите первое число" v-model="argumentOne">
        </form>
        <div class="form_radio_group">
            <div class="form_radio_group-item">
                <input id="radio-1" type="radio" name="radio" value="1" @click ='operator="/"'>
                <label for="radio-1">/</label>
            </div>
            <div class="form_radio_group-item">
                <input id="radio-2" type="radio" name="radio" value="2" @click ='operator="х"'>
                <label for="radio-2">х</label>
            </div>
            <div class="form_radio_group-item">
                <input id="radio-3" type="radio" name="radio" value="3" @click ='operator="-"'>
                <label for="radio-3">-</label>
            </div>
            <div class="form_radio_group-item">
                <input id="radio-4" type="radio" name="radio" value="4" @click ='operator="+"'>
                <label for="radio-4">+</label>
            </div>
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
                case 'х':
                    this.result = this.argumentOne * this.argumentTwo;
                    break;
                case '-':
                    this.result = this.argumentOne - this.argumentTwo;
                    break;
                case '+':
                    this.result = this.argumentOne + this.argumentTwo;
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

    .form_radio_group {   
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        align-items: flex-start;
        align-content: flex-start;
        gap: 3px;
    }

    .form_radio_group-item  {
        font-size: 20px;
        background: #D9D9D9;
        box-shadow: inset 2px 2px 5px 1px rgba(0, 0, 0, 0.25);
        border: none;           
    }

    .form_radio_group label {
        display: flex;
        width: 30px;
        height: 30px;
        align-items: center;
        justify-content: center;
        cursor: pointer;
    }

    .form_radio_group input[type=radio] {
        display: none;
    }
    
    .form_radio_group input[type=radio]:checked + label {
        background-color: #FFCDD2;
    }

    .form_radio_group label:hover {
        background-color: #EF5350;
    }

  </style>
  