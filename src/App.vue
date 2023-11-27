<script setup>
import { reactive } from "vue";

const estado = reactive({
  numero1: 0,
  numero2: 0,
  expresao: "adicao"
});

function calcula() {
  if (estado.expresao === "adicao") {
    return Number(estado.numero1) + Number(estado.numero2);
  } else if (estado.expresao === "subtracao") {
    return estado.numero1 - estado.numero2;
  } else if (estado.expresao === "multiplicacao") {
    return estado.numero1 * estado.numero2;
  } else {
    return estado.numero1 / estado.numero2;
  }
}
</script>

<template>
  <div
    class="relative container w-full max-w-2xl mx-auto my-20 bg-cyan-800 py-20 rounded"
  >
    <h1 class="text-center text-5xl font-bold text-white">Calculadora</h1>
    <div class="container mt-8 mx-auto">
     
      <input
        @keyup="(evento) => (estado.numero1 = evento.target.value)"
        class="rounded mt-4 border-b w-2/5 ml-28 p-2"
        type="number"
        placeholder="Valor1"
      />

      <select
        @change="(evento) => (estado.expresao = evento.target.value)"
        name="select"
        id="operadores"
        class="flex absolute rounded p-2 font-bold w-12 right-9 sm:w-36 top-44 sm:right-30"
      >
        <option value="adicao">+ Adição</option>
        <option value="subtracao">- Subtração</option>
        <option value="multiplicacao">x Multiplicação</option>
        <option value="divisao">/ Divisão</option>
      </select>
      <br />
      <input
        @keyup="(evento) => (estado.numero2 = evento.target.value)"
        class="rounded mt-4 border-b w-2/5 ml-28 p-2"
        type="number"
        placeholder="Valor2"
      />

    
    </div>
    <h2 class="text-center text-white font-bold text-3xl mt-16">Resultado</h2>
    <h2 class="text-center text-white font-bold text-3xl mt-4">{{ calcula()}}</h2>
  </div>
</template>

<style scoped></style>
