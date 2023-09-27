<script setup>
import { reactive } from "vue";
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';

const estado = reactive({
  valor1: 0,
  valor2: 0,
  resultado: 0,
  operacao: '+',
});

function calcular() {
  estado.valor1 = parseFloat(estado.valor1);
  estado.valor2 = parseFloat(estado.valor2);

  if (estado.operacao != '') {

    if (estado.operacao === '+') {
        estado.resultado = estado.valor1 + estado.valor2;
      } else if (estado.operacao === '-') {
          estado.resultado = estado.valor1 - estado.valor2;
      } else if (estado.operacao === '*') {
          estado.resultado = estado.valor1 * estado.valor2;
      } else if (estado.operacao === '/') {
          if (estado.valor2 != 0 ) {
            estado.resultado = (estado.valor1 / estado.valor2);
          } else if (estado.resultado === '' || estado.resultado === '0') { 
            estado.resultado = "";
          }
      }    
  }

  if (estado.resultado > 0) {
    estado.resultado = estado.resultado.toFixed(2);
  }
}

function alteraValor1(evento) {
  estado.valor1 = evento.target.value;
  calcular();
}

function escolheOperacao(evento) {
  estado.operacao = evento.target.value

  calcular();
}

function alteraValor2(evento) {
  estado.valor2 = evento.target.value;
  
  if (estado.operacao != '/' || (evento.target.value != 0 && evento.target.value != '')){
    calcular();
  } else {
      estado.resultado = 0;
      if (evento.target.value != '') {
        alert('Na divisão, o segundo valor não pode ser zero!');
      }
  }
}
</script>

<template>
  <body>
    <div class="container">
      <Cabecalho />
      <Formulario 
        :calcular="calcular" 
        :alteraValor1="alteraValor1" 
        :alteraValor2="alteraValor2" 
        :escolhaOperacao="escolheOperacao"
        :operacao="estado.operacao"
        :valor2="estado.valor2"
        :resultado="estado.resultado"/>
    </div>
  </body>
</template>

<style scoped>
  body{
    background-image: url(./images/mathematics-1509559_1280.jpg);
    background-size: contain;
    background-color: transparent;
    display: flex;
    width: 100vw;
    height: 100vh;
    align-items: center;
  }  
  .container {
    background-color: transparent;
    color:white;
    border-radius: 16px;
    padding-top: 50px;  
    padding-bottom: 50px;
    text-align: center;
  }
</style>