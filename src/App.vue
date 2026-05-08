<template>
<ProductForm @agregar="agregarProducto"/>
<select v-model="filtro">
    <option value="Todos">Todos</option>
    <option value="Electrónica">Electrónica</option>
    <option value="Ropa">Ropa</option>
    <option value="Hogar">Hogar</option>
    <option value="Indumentaria">Indumentaria</option>
    <option value="Deportes">Deportes</option>
    <option value="Alimentos">Alimentos</option>
</select>
<ProductList :productos="productosFiltrados" @eliminar="eliminarProducto" />
<p>Cantidad de productos: {{ productos.length }}</p>
<p>Valor total del inventario: ${{ valorInventario }}</p>

</template>
<script setup>
import { computed, ref } from 'vue'
import ProductForm from './ProductForm.vue';
import ProductList from './ProductList.vue';

const productos = ref([])
let inicioId = 1

function agregarProducto(producto) {
    productos.value.push({ id: inicioId, ...producto }) 
    inicioId++
}

function eliminarProducto(id) {
    productos.value = productos.value.filter(producto => producto.id !== id) // Busca el valor del id filtrado y lo elimina del array de productos
}

const filtro = ref('Todos')
const productosFiltrados = computed(() => {
    if (filtro.value === 'Todos') {
        return productos.value
    } else {
        return productos.value.filter(producto => producto.categoria === filtro.value)
    }
})

const valorInventario = computed(() => {
    return productos.value.reduce((total, producto) => total + (producto.precio * producto.stock), 0)
})

</script>