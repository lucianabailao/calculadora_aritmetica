<script setup>
import { reactive } from 'vue';

const calc = reactive({
  num1: '0',
  num2: '0',
  operacao: 'somar',
})

function resultado(){
  const {operacao} = calc

  switch(operacao){
    case 'subtrair': return parseInt(calc.num1) - parseInt(calc.num2)
    case 'multiplicar': return parseInt(calc.num1) * parseInt(calc.num2)
    case 'dividir': return parseInt(calc.num1) / parseInt(calc.num2)

    default : return parseInt(calc.num1) + parseInt(calc.num2)
  }
}
</script>

<template>
  <header class="p-5 mb-4 mt-4 bg-light rounded-3">
    <div class="container">
    <h1 class="text-center">Calculadora Aritmética</h1>
  </div>
  </header>
  <br/>
  <hr/>
    <div class="row">
      <input type="number" class="form-control col text-center" placeholder="Número 1" @keyup="evento => calc.num1 = evento.target.value">
      <select class="form-control col-2 col-md text-center" @change="evento => calc.operacao = evento.target.value">
        <option value='somar'>+</option>
        <option value='subtrair'>-</option>
        <option value='multiplicar'>x</option>
        <option value='dividir'>÷</option>
      </select>
      <input type="number" class="form-control col text-center" placeholder="Número 2" @keyup="evento => calc.num2 = evento.target.value">
    </div>

    <div class="mt-5 text-center">
      <h3>{{resultado()}}</h3>
    </div>
    <br/>
  <hr/>
</template>

<style scoped>

</style>
