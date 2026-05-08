<template>
<div>
    <h1>Lista de Productos</h1>
    <ul>
        <ProductItem v-for="producto in productos"
        :key="producto.id" 
        :producto="producto"
        @eliminar="$emit('eliminar', $event)"
        />
    </ul>
</div>

</template>
<script setup>
import ProductItem from './ProductItem.vue'

const props = defineProps({
    productos: {
        type: Array,
        required: true
    }
})

const emit = defineEmits(['eliminar'])
</script>