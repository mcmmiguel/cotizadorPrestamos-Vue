<script setup>
  import {ref, computed} from 'vue';
  import Header from './components/Header.vue';

  const minCantidad = 0;
  const maxCantidad = 20000;
  const stepCantidad = 100;

  const cantidad = ref(10000);

  const formatearDinero = computed( () => {
    const formatter = new Intl.NumberFormat('en-US', {
      style: 'currency',
      currency: 'USD',
    });

    return formatter.format(cantidad.value);
  });

  const handleChangeDecremento = (e) => {
    if(cantidad.value <= minCantidad) return;
    cantidad.value -= stepCantidad;
  }
  
  const handleChangeIncremento = (e) => {
    if(cantidad.value >= maxCantidad) return;
    cantidad.value += stepCantidad;
  }

</script>

<template>
  <div class="my-20 max-w-lg mx-auto bg-white shadow p-10">
    <Header />

    <div class="flex justify-between mt-10">
      <button 
        class="h-10 w-10 flex items-center justify-center font-bold bg-lime-500 rounded-full hover:outline-none hover:ring-2 hover:ring-offset-2 hover:ring-lime-500 text-white text-2xl"
        @click="handleChangeDecremento"
      >
        -
      </button>
      
      <button 
        class="h-10 w-10 flex items-center justify-center font-bold bg-lime-500 rounded-full hover:outline-none hover:ring-2 hover:ring-offset-2 hover:ring-lime-500 text-white text-2xl"
        @click="handleChangeIncremento"
      >
        +
      </button>
    </div>

    <div class="my-5">
      <input 
        class="w-full bg-gray-200 accent-lime-500 hover:accent-lime-600" 
        type="range"
        :min="minCantidad"
        :max="maxCantidad"
        :step="stepCantidad"
        v-model.number="cantidad"
        >
      <p class="text-center my-10 text-5xl font-extrabold text-indigo-600">{{formatearDinero}}</p>
    </div>
  </div>
</template>


