<script setup>
import { ref, computed } from 'vue';
import Resultado from './Resultado.vue';



const numero1 = ref();
const numero2 = ref();
const operacao = ref('');


const atualizarNumero1 = (event) => {
  numero1.value = parseFloat(event.target.value); 
};

const atualizarNumero2 = (event) => {
  numero2.value = parseFloat(event.target.value);
};


const atualizarOperacao = (event) => {
  operacao.value = event.target.value;
};


const opcoes = [
  { texto: 'Soma', valor: 'soma' },
  { texto: 'Subtração', valor: 'subtracao' },
  { texto: 'Multiplicação', valor: 'multiplicacao' },
  { texto: 'Divisão', valor: 'divisao' }
];


const resultado = computed(() => {
  switch (operacao.value) {
    case 'soma':
      return numero1.value + numero2.value;
    case 'subtracao':
      return numero1.value - numero2.value;
    case 'multiplicacao':
      return numero1.value * numero2.value;
    case 'divisao':
      return numero2.value !== 0 ? numero1.value / numero2.value : 'Não pode dividir por zero';
    default:
      return 'adicione números';
  }
});

</script>

<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-12 col-md-12 d-flex justify-content-center">
        <form class="form-control d-flex flex-column align-items-center">
          <input :value="numero1" @input="atualizarNumero1" class="rounded m-2" type="number" placeholder="Digite um número" />
          <input :value="numero2" @input="atualizarNumero2" class="rounded m-2" type="number" placeholder="Digite um número" />
          <select :value="operacao" @change="atualizarOperacao" class="btn btn-light rounded m-2">
            <option v-for="opcao in opcoes" :key="opcao.valor" :value="opcao.valor">
              {{ opcao.texto }}
            </option>
          </select>
        </form>       
      </div>
    </div>
  </div>
  <Resultado :resultado="resultado"/>
  
</template>

