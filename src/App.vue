<script setup>
// const arrayfrutas = [
//   {
//     name: "Manzana",
//     price: "1",
//     descripcion: "Una Manzana",
//     stock: "20"
//   },
//   {
//     name: "Pera",
//     price: "2",
//     descripcion: "Una pera",
//     stock: "0"
//   },
//   {
//     name: "Durazno",
//     price: "3",
//     descripcion: "Un durazno",
//     stock: "0"
//   }
// ]
// const objetoFruta = {
//   name: "Manzana",
//   price: "1 USD",
//   descripcion: "Una Manzana",
//   id: 1
// }
// const handleClick = (mensaje) => {
//   console.log(mensaje)
// }

import { ref, computed } from 'vue';
const name = "Vue Dinamico"
const arrayColores = ["green", "red", "green"]
const activo = false
const arrayNumeros = ref([]);

const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'zero'
  }
  if (counter.value > 0) {
    return 'positive'
  }
  if (counter.value < 0) {
    return 'negative'
  }
})

const counter = ref(0);

const increment = (increment) => {
  if (increment) {
    counter.value++;
  } else {
    counter.value--;
  }

}
const reset = () => {
  counter.value = 0
}

const addNumber = () => {
  arrayNumeros.value.push(counter.value);
}

const enabledDisabled = computed(() => {
  return arrayNumeros.value.includes(counter.value);
})
</script>
<template>
  <div class="container">
    <h1>Hola {{ name }}</h1>
    <br>
    <h2 :class="classCounter">Contador: {{ counter }}</h2>
    <br>
    <div class="btn-group">
      <button @click="increment(true)" class="btn btn-outline-success">
        Aumentar
      </button>
      <button @click="increment(false)" class="btn btn-outline-danger">
        Disminuir
      </button>
      <button @click="reset()" class="btn btn-outline-warning">
        Reiniciar
      </button>
      <button :disabled="enabledDisabled" @click="addNumber()" class="btn btn-primary">
        Agregar
      </button>
    </div>
    <div class="div">
      <ul class="list-group list-group-flush">
        <li v-for="number in arrayNumeros" class="list-group-item">
          {{ number }}
        </li>
      </ul>
    </div>
  </div>



  <!-- <button v-on:click.right.prevent="handleClick('Clic 1 Derecha')">
    Activame 1
  </button>
  <button @click.left="handleClick('Clic 2 Izquierda')">
    Activame 2
  </button>
  <button @click.middle="handleClick('Clic 3 Centro')">
    Activame 3
  </button> -->
  <!-- <ul> -->
  <!-- <li v-for="(fruta) in arrayfrutas" :key="fruta.name">Nombre: {{fruta.name}}, Precio: {{ fruta.price }} USD, Descripcion: {{ fruta.descripcion }}</li> Recorrer arrays -->
  <!-- <li v-for="(value, propiedad, index) in objetoFruta" :key="value">{{ index }} {{ propiedad }} : {{ value }}</li> Recorrer objetos -->
  <!-- <template v-for="(item) in arrayfrutas" :key="item.name">
      <li v-if="item.stock > 0">
        {{ item.name }} - {{ item.price }}
    </li>
    </template> -->

  <!-- </ul> -->
</template>
<style>
.positive {
  color: green;
}

.negative {
  color: red;
}

.zero {
  color: peru;
}
</style>
