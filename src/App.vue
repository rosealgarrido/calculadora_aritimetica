<script setup>
  
  
  function somar() {
    var n1 = parseInt(document.getElementById('n1').value);
    var n2 = parseInt(document.getElementById('n2').value);
    document.getElementById('resultado').innerHTML = n1 + n2;
  }

  function subtrair() {
    var n1 = parseInt(document.getElementById('n1').value);
    var n2 = parseInt(document.getElementById('n2').value);
    document.getElementById('resultado').innerHTML = n1 - n2;
  }

  function multiplicar() {
    var n1 = parseInt(document.getElementById('n1').value);
    var n2 = parseInt(document.getElementById('n2').value);
    document.getElementById('resultado').innerHTML = n1 * n2;
  }

  function dividir() {
    var n1 = parseInt(document.getElementById('n1').value);
    var n2 = parseInt(document.getElementById('n2').value);
    document.getElementById('resultado').innerHTML = n1 / n2;
  }
</script>

<template>
  <div class="container">
    <header>
      <h1>Calculadora Aritmética</h1>
    </header>
  </div>
  <form>
    <div class="row">
      <div @onclick="resultado" class="col-md-2">
        <input type="number" placeholder="Digite o primeiro número" class="form-control" id="n1">
      </div>
      <div class="col-md-2">
        <select id="operador">
          <option value="adicao" v-if="adicao => somar()">Adição</option>
          <option value="subtracao" v-if="subtracao => subtrair()">Subtração</option>
          <option value="multiplicacao" v-if="multiplicacao => multiplicar()">Multiplicação</option>
          <option value="divisao" v-if="divisao => dividir()">Divisão</option>
        </select>
      </div>
    <div class="col-md-2">
      <input type="number" placeholder="Digite o segundo número" id="n2">
    </div>
    <div class="col-md-2">
      <input type="number" id="resultado" placeholder="Resultado"></div>
    </div>
  </form>

</template>

<style scoped>
  
</style>
