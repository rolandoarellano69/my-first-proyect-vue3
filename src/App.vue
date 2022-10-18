<script setup>
import { ref, computed } from "vue";
const name = "Vue 3";
const counter = ref(0);
const title = "contador ";
const arrayCounter = ref([]);

//contador para el incremento
const increment = () => {
  counter.value++;
};

//contador para el decremento
const decrement = () => {
  counter.value--;
};

//Contador para el reseteo
const reset = () => {
  counter.value = 0;
};
//funcion del boton agregar
const add = () => {
  arrayCounter.value.push(counter.value);
};
//funcion del boton Agregar para que se desactive y no se repita
const blockNumber = computed(() => {
  const number = arrayCounter.value.find((num) => num === counter.value);
  return number || number === 0;
});

const classCounter = computed(() => {
  if (counter.value === 0) {
    return "zero";
  }
  return counter.value > 0 ? "positive" : "negative";
});
</script>

<template>
  <div class="container text-centeer mt-5">
    <h1>Hola {{ name }} {{ title }}!</h1>
    <h2 :class="classCounter">
      {{ counter }}
    </h2>

    <div class="btn-group" role="group" aria-label="Basic example">
      <button @click="increment" class="btn btn-success">Increment</button>
      <button @click="decrement" class="btn btn-danger">Decrement</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="add" :disabled="blockNumber" class="btn btn-primary">
        Add
      </button>
    </div>
    <h2 class="mt-3">Mis Favoritos</h2>
    <ul class="list-group mt-2">
      <li
        class="list-group-item"
        v-for="(item, index) in arrayCounter"
        :key="index"
      >
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<style>
button {
  margin: 4px 2px;
  cursor: pointer;
}
.negative {
  color: red;
}

.positive {
  color: green;
}
.zero {
  color: blueBright;
}
</style>

//minuto 1:13:47
