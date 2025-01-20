<script setup>

    const props = defineProps({
        alerta: {
            type: Object,
            required: true
        }
    })

</script>


<template>
    <div
        class="text-white text-center p3 uppercase folt-bold mb-3 rounded-md bg-red-500"
    >
        <p>{{alerta.mensaje}}</p>
    </div>
</template>