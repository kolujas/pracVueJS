<script setup>
import {ref, computed} from 'vue'

// PRIMER DESAFIO

const cont = ref(0);

const incrementar = () => {
  cont.value++;
}

const disminuir = () => {
  cont.value--;
}

const resetear = () => {
  cont.value = 0;
}

const classCont = computed(() => {
  if(cont.value === 0){
    return 'zero';
  }

  if(cont.value > 0){
    return 'mayor';
  }

  if(cont.value < 0){
    return 'menor';
  }
  
})

const numFavs = ref([]);

// agarro el valor del array y pusheo el valor de contador

const agregar = () => {
  numFavs.value.push(cont.value);
}

// El valor del array INCLUYE el valor del contador
const bloquear = computed(() => {
  const number = numFavs.value.includes(cont.value);
  return number || number === 0;
});



</script>

<template>
  <h1 class="text-4xl pl-8 uppercase pt-2">Practiqueta VUE</h1>
  <!-- Mi version -->
  <!-- <h3 class="text-2xl pl-4 pt-12">Version Kolo</h3>
  <div>
    <button @click="incrementar" class="bg-blue-400 text-white rounded p-2 mt-8 ml-16">Incrementar</button>
    <button @click="disminuir" class="bg-blue-400 text-white rounded p-2 mt-8 ml-16">Disminuir</button>
    <button @click="resetear" class="bg-blue-400 text-white rounded p-2 mt-8 ml-16">Resetear</button>
    <p v-if="cont < 0" class="mt-8 ml-16 text-red-600">{{cont}}</p>
    <p v-if="cont > 0" class="mt-8 ml-16 text-green-600">{{cont}}</p>
    <p v-else-if="cont === 0" class="mt-8 ml-16 text-black">{{cont}}</p>
  </div> -->

  <!-- Mejoras con operador ternario -->
  <h3 class="text-2xl pl-4 pt-12">Version Bluuweb</h3>
  <button @click="incrementar" class="bg-blue-400 text-white rounded p-2 mt-8 ml-16">Incrementar</button>
  <button @click="disminuir" class="bg-blue-400 text-white rounded p-2 mt-8 ml-16">Disminuir</button>
  <button @click="resetear" class="bg-blue-400 text-white rounded p-2 mt-8 ml-16">Resetear</button>
  <!-- disabled (funcion) -->
  <button @click="agregar" :disabled="bloquear" class="bg-blue-400 text-white rounded p-2 mt-8 ml-16">Agregar</button>
  <p :class="classCont" class="mt-8 ml-16 font-bold">{{cont}}</p> <br>
    <ul>
           <li v-for="(item, index) in numFavs" :key="index"> <!-- Recorro el array -->
              {{ item }}
          </li>
    </ul>

</template>

<style>
.mayor{
  color: green;
}

.menor{
  color: red;
}

.zero{
  color: fuchsia;
}
</style>