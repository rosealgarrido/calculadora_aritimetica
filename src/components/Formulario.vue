<script setup>
    const props = defineProps(['calcular','alteraValor1', 'alteraValor2', 'escolhaOperacao', 'operacao','valor2', 'resultado']);
</script>
<template>
    <form @submit.prevent="props.calcular">
        <input required @keyup="props.alteraValor1" class="form-control" type="number" step=".01" placeholder="Valor 1" />
        <select class="form-select escolha" @change="props.escolhaOperacao">
            <option selected value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
        </select>
        <input required @keyup="props.alteraValor2" class="form-control" 
        :class="{ invalido: props.operacao == '/' && (props.valor2 === 0 || props.valor2 === '')}" type="number" step=".01" placeholder="Valor 2" />
        <span class="igual">=</span>
        <input readonly disabled :value="props.resultado" class="form-control" 
        :class="{ invalido: props.operacao == '/' && (props.valor2 === 0 || props.valor2 === '')}" type="number" step=".01"/>
        <button class="btn btn-primary btn__calcular" type="submit">Calcular</button>
    </form>
</template>
<style scoped>
    form{
        display: inline-flex;
        font-size: 30px;
    }
    input{
        color: white;
        max-width: 130px;
        background-color: #309d9a;
        font-weight: bold;
        text-align: center;
        margin: 0;
    
        &:hover{
            background-color: #309d9a;
            border-color: #309d9a;
            outline-color: #309d9a;
        }

        &:disabled{
            background-color: #309d9a;
            border-color: #309d9a;
            outline-color: #309d9a;
        }
            
        &::placeholder {
        color: white;
        }
    }
    
    /*Retira as setas do input numérico*/
    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
        -webkit-appearance: none;
        margin: 0;
    }

    input[type=number] {
        -moz-appearance: textfield;
    }

    input.invalido,
    input:disabled.invalido {
        outline-color: red;
        border-color: red;
    }
    .escolha{
        background-color: #309d9a;
        color: white;
        background-color: #309d9a;
        min-width: 60px;
        max-width: 60px;
        margin: 0px 10px;
        &:focus{
            background-color: white;
            color: black;
        }
    }
    .igual {
        margin: 0px 5px;
    }
    .btn__calcular {
        background-color: #309d9a;
        border-color: white;
        outline-color: white;
        margin-left: 20px;
        &:hover{
            background-color: #309d9a;
            border-color:#309d9a;
            outline-color: white;
        }
    }    
</style>