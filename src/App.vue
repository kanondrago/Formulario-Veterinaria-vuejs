
<script setup>

  import { ref, reactive } from 'vue';
  
  import Header from './components/Header.vue'
  import Formulario from './components/Formulario.vue';

  const pacientes = ref([]);

  const paciente = reactive({
        nombre: 'Ronald',
        propietario: 'Oscar',
        email: 'oscar@mail.com',
        alta: '2025-03-20',
        sintomas: 'Ingesta de producto químico',
  });

</script>

<template>
  <div class="container mx-auto mt-20">
    <Header></Header>

    <div class="mt-12 md:flex">
      <Formulario 
        v-model:nombre="paciente.nombre"
        v-model:propietario="paciente.propietario"
        v-model:email="paciente.email"
        v-model:alta="paciente.alta"
        v-model:sintomas="paciente.sintomas"
      ></Formulario>

      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Administra tus pacientes</h3>

        <div v-if="pacientes.length > 0">

        </div>

        <div v-else>
          <h2 class="text-center text-2xl mt-20 font-bold">No hay pacientes</h2>
        </div>

      </div>
    </div>

  </div>
</template>
