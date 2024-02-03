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

    return formatter.format(cantidad.value)
  });

</script>

<template>
  <div class="my-20 max-w-lg mx-auto bg-white shadow p-10">
    <Header />

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


