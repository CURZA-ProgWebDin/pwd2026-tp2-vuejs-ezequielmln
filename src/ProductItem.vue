<template>
    <li> 
         Id: {{ producto.id }} -
         Nombre: {{ producto.nombre }} -
         Precio: ${{ producto.precio }} -
         Stock: {{ producto.stock }} - 
         Categoria: {{ producto.categoria }}
    <button @click="$emit('eliminar', producto.id)">Eliminar</button>
    </li>
</template>
<script setup>
const emit =defineEmits(['eliminar'])
const props = defineProps({
    producto: {
        type: Object,
        required: true
    }
})
</script>