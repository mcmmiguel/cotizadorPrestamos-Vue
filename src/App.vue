<script setup>
  import {ref} from 'vue';
  import Header from './components/Header.vue';

  const minCantidad = 0;
  const maxCantidad = 20000;
  const stepCantidad = 100;

  const cantidad = ref(10000);

  function handleChange(e) {
    cantidad.value = Number(e.target.value);
  }
</script>

<template>
  <div class="my-20 max-w-lg mx-auto bg-white shadow p-10">
    <Header />

    <div class="my-5">
      <input 
        @input="handleChange" 
        class="w-full bg-gray-200 accent-lime-500 hover:accent-lime-600" 
        :value="cantidad"
        type="range"
        :min="minCantidad"
        :max="maxCantidad"
        :step="stepCantidad"
        >
      {{ cantidad }}
    </div>
  </div>
</template>


