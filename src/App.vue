<script setup lang="ts">
import { reactive, watch } from 'vue'
import Header from './components/Header.vue'
import Valores from './components/Valores.vue'
import Resultado from './components/Resultado.vue'

interface State {
  valor1: number | null
  valor2: number | null
  operador: string | null
  resultado: number | string
}

const state = reactive<State>({
  valor1: null,
  valor2: null,
  operador: '+',
  resultado: 0 || '',
})

function calcularResultado() {
  if (state.valor1 === null || state.valor2 === null) {
    state.resultado = 'Por favor, insira ambos os valores.'
    return
  }
  
  switch (state.operador) {
    case '+':
      state.resultado = `Resultado = ${state.valor1 + state.valor2}`
      break
    case '-':
      state.resultado = `Resultado = ${state.valor1 - state.valor2}`
      break
    case '*':
      state.resultado = `Resultado = ${state.valor1 * state.valor2}`
      break
    case '/':
      state.resultado = state.valor1 === 0 || state.valor2 === 0 ? 'Impossível dividir por 0' : `Resultado = ${state.valor1 / state.valor2}`
      break
    default:
      state.resultado = 'Operador inválido!'
  }
}

watch(
  () => [state.valor1, state.valor2, state.operador],
  calcularResultado
)
</script>

<template>
  <div class="container-fluid">
    <Header></Header>
    <Valores :valor1="state.valor1" :valor2="state.valor2" :operador="state.operador"
      @update:valor1="state.valor1 = $event" @update:valor2="state.valor2 = $event"
      @update:operador="state.operador = $event" />
    <Resultado :resultado="state.resultado" />
  </div>
</template>

<style lang="scss" scoped>
  @import "@/styles/custom-bootstrap.scss";

  div {
    background-color: $background-principal;
  }
</style>