<script>
import { reactive } from 'vue';

export default {
  setup() {
    const estadoInicial = reactive({
      num1: 0,
      num2: 0,
      operator: '+',
      result: 0
    });

    const calculate = () => {
      switch (estadoInicial.operator) {
        case '+':
          estadoInicial.result = parseFloat(estadoInicial.num1) + parseFloat(estadoInicial.num2);
          break;
        case '-':
          estadoInicial.result = parseFloat(estadoInicial.num1) - parseFloat(estadoInicial.num2);
          break;
        case '*':
          estadoInicial.result = parseFloat(estadoInicial.num1) * parseFloat(estadoInicial.num2);
          break;
        case '/':
          estadoInicial.result = parseFloat(estadoInicial.num1) / parseFloat(estadoInicial.num2);
          break;
        default:
          estadoInicial.result = 0;
      }
    }

    return { estadoInicial, calculate };
  }
}
</script>

<template>
    <div class="container mt-5 bg-light p-4">
        <h1 class="mb-4">Calculadora Aritmética</h1>
        <div class="row">
            <div class="col">
            <label for="number1" class="form-label">Número:</label>
            <input type="number" class="form-control" v-model="estadoInicial.num1" id="number1" @input="calculate">
        </div>
        <div class="col">
        <label for="number2" class="form-label">Número:</label>
        <input type="number" class="form-control" id="number2" v-model="estadoInicial.num2" @input="calculate">
        </div>
        <div class="col">
        <label class="form-label">Operação:</label>
        <select class="form-select" v-model="estadoInicial.operator" @change="calculate">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>
      </div>
    
      <div class="col">
        <h3 class="mt-4">= {{ estadoInicial.result }}</h3>
      </div>
    </div>
  </div>
</template>
