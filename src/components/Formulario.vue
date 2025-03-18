<script setup>

    import { reactive, ref } from 'vue';
    import Alerta from './Alerta.vue';
    
    const alerta = reactive({
        tipo: '',
        mensaje: '',
    })

    // Eventos por donde escuchara
    defineEmits(['update:nombre', 'update:propietario', 'update:email', 'update:alta', 'update:sintomas'])

    // Props 
    const props = defineProps({
        nombre: {
            type: String,
            required: true,
        }, 
        propietario: {
            type: String,
            required: true,
        }, 
        email: {
            type: String,
            required: true,
        }, 
        alta: {
            type: String,
            required: true,
        }, 
        sintomas: {
            type: String,
            required: true,
        }
    })

    const validar = (event) => {

        // console.log('Mira tu....',Object.values(paciente))
        // Muy interesante que se puede validar los props
        if(Object.values(props).includes('')) {
            alerta.mensaje = 'Todos los campos son obligatorios';
            alerta.tipo = 'error';
            console.log('alerta', alerta);
            return;
        }

        alerta.mensaje = 'Todos los campos agregados correctamente';
        alerta.tipo = 'exito';
        
        console.log('alerta', alerta);
        console.log('Agregando a la base de datos');
    }


</script>


<template>

    <div class="md:w-1/2">
        <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>
        <p class="text-lg mt-5 text-center mb-10">
            Añade Pacientes
            <span class="text-indigo-600 font-bold">Administralos</span>
        </p>

        <Alerta
            v-if="alerta.mensaje"
            v-bind:alerta="alerta"
        >

        </Alerta>

        <form 
            class="bg-white shadow-2xl rounded-lg py-10 px-5"
            v-on:submit.prevent="validar($event)">

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
                    @input="$emit('update:nombre', $event.target.value)"
                    :value="nombre"                    
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
                    v-on:input="$emit('update:propietario', $event.target.value)"
                    :value="propietario"
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
                    @input="$emit('update:email', $event.target.value)"
                    :value="email"
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
                    @input="$emit('update:alta', $event.target.value)"
                    :value="alta"
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
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
                    @input="$emit('update:sintomas', $event.target.value)"
                    :value="sintomas"
                >
                </textarea>
            </div>

            <input 
                type="submit"
                value="Registrar Paciente"
                class="bg-indigo-400 w-full p-3 text-white uppercase font-bold cursor-pointer hover:bg-indigo-700 transition-colors rounded-md"
            >

        </form>

    </div>

</template>