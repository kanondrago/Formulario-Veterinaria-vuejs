<script setup>

    import { ref } from 'vue';

    const nombre = ref('');

    const leerNombre = (event) => {
        nombre.value = event.target.value;
    }

</script>


<template>

    <div class="md:w-1/2">
        <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>
        <p class="text-lg mt-5 text-center mb-10">
            Añade Pacientes
            <span class="text-indigo-600 font-bold">Administralos</span>
        </p>

        <form class="bg-white shadow-2xl rounded-lg py-10 px-5">
            <div class="mb-5">
                <label 
                    class="block text-gray-700 uppercase font-bold"
                    for="mascota">
                    Nombre de la mascota
                </label>
                <input 
                    id=mascota 
                    type="text" 
                    placeholder="Nombre de la mascota"
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
                    v-bind:value="nombre"
                    v-on:input="leerNombre($event)"
                >
            </div>

            <div class="mb-5">
                <label 
                    class="block text-gray-700 uppercase font-bold mt-4"
                    for="propietario">
                    Nombre del propietario
                </label>
                <input 
                    id=propietario 
                    type="text" 
                    placeholder="Nombre de propietario"
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
                >
            </div>

            <div class="mb-5">
                <label 
                    class="block text-gray-700 uppercase font-bold mt-4"
                    for="email">
                    Email de propietario
                </label>
                <input 
                    id=email 
                    type="email" 
                    placeholder="Email de propietario"
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
                >
            </div>

            <div class="mb-5">
                <label 
                    class="block text-gray-700 uppercase font-bold mt-4"
                    for="alta">
                    Alta
                </label>
                <input 
                    id=alta 
                    type="date" 
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
                >
            </div>

            <div class="mb-5">
                <label 
                    class="block text-gray-700 uppercase font-bold mt-4"
                    for="sintomas">
                    Sintomas
                </label>
                <textarea
                    id=sintomas 
                    placeholder="Descrine los sintomas de los pacientes"
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40">
                </textarea>
            </div>

            <input 
                type="submit"
                value="Registrar Paciente"
                class="bg-indigo-400 w-full p-3 text-white uppercase font-bold cursor-pointer hover:bg-indigo-700 transition-colors rounded-md">

        </form>

    </div>

</template>