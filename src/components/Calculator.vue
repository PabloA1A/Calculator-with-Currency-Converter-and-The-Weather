<script setup>
import { ref } from 'vue'

// Estado para el display
const display = ref('')

// Función para manejar el clic de los botones
function handleClick(value) {
  display.value += value
} 
// Función para limpiar el display
function clearDisplay() {
  display.value = ''
}

//Funcion 

  function result () {
  try {
    display.value = eval(display.value)
  } catch (e) {
    display.value = 'Error'
  }
} 
  
</script>

<template>
  <div>
    <div class="calculator">
            <input type="text" id="display" :value="display">
            <div class="buttons">
                <button @click="handleClick('7')">7</button>
                <button @click="handleClick('8')">8</button>
                <button @click="handleClick('9')">9</button>
                <button @click="handleClick('+')">+</button>
                <button @click="handleClick('4')">4</button>
                <button @click="handleClick('5')">5</button>
                <button @click="handleClick('6')">6</button>
                <button @click="handleClick('-')">-</button>
                <button @click="handleClick('1')">1</button>
                <button @click="handleClick('2')">2</button>
                <button @click="handleClick('3')">3</button>
                <button @click="handleClick('*')">*</button>
                <button @click="handleClick('.')">.</button>
                <button @click="handleClick('0')">0</button>
                <button @click="result">=</button>
                <button @click="handleClick('/')">/</button>
                <button class="ce" @click="clearDisplay">CE</button>

            </div>
        </div>
  </div>
</template>

<style scoped lang="scss">


.calculator {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);


    #display {
        width: 100%;
        height: 50px;
        margin-bottom: 10px;
        text-align: right;
        padding-right: 10px;
        font-size: 18px;
        border: 1px solid #ddd;
        border-radius: 5px;
    }

    .buttons {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 10px;


            button {
                padding: 20px;
                font-size: 18px;
                border: none;
                border-radius: 5px;
                cursor: pointer;
                background-color: #007bff;
                color: #fff;
            }
            .ce{
              background-color: red
            }

            button:hover {
                background-color: #0056b3;
            }
    }

}


   

</style>