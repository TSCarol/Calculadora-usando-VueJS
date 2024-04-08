<script>
  export default {
    data() {
      return {
        numero1: 0,
        numero2: 0,
        operator: '+',
        resultOperations: null
      };
    },
    methods: {
      calculate() {
        switch(this.operator) {
          case '+':
            this.resultOperations = parseFloat(this.numero1) + parseFloat(this.numero2);
            break;
          case '-':
            this.resultOperations = parseFloat(this.numero1) - parseFloat(this.numero2);
            break;
          case '*':
            this.resultOperations = parseFloat(this.numero1) * parseFloat(this.numero2);
            break;
          case '/':
            this.resultOperations = parseFloat(this.numero1) / parseFloat(this.numero2);
            break; 
        }
      }
    }
  };
</script>

<template>
  <div class="container">
    <input class="numeros" type="number" v-model="numero1" @input="calculate">
    <select v-model="operator" @change="calculate">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    <input class="numeros" type="number" v-model="numero2" @input="calculate">
    <div class="resultOperations" v-if="resultOperations !== null">
      <template v-if="numero1 !== 0 && numero2 !== 0">
        O resultado da operação é {{ resultOperations }}
      </template>
    </div>
  </div>
</template>

<style scoped>
  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #67827e;
  }

  .numeros,
  select {
    margin: 20px;
    padding: 10px;
    font-size: 18px;
    border-radius: 10px;
    background-color: #fff;
    border: 2px solid #283836;
    text-align: center;
  }

  .numeros {
    width: 200px;
  }

  select {
    width: 5%;
  }

  .resultOperations {
    margin-top: 10px;
    font-size: 20px;
    padding: 10px 20px;
    border-radius: 10px;
    background-color: #fff;
    border: 2px solid #283836;
  }
</style>
