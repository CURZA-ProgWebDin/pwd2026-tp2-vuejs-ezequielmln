<template>
<form @submit.prevent="enviar">
    <label for="nombre">Nombre</label>
    <input type="text" id="nombre" v-model="nombre">
    <label for="precio">Precio</label>
    <input type="number" id="precio" v-model="precio" min="0">
    <label for="stock">Stock</label>
    <input type="number" id="stock" v-model="stock" min="0">

    <label for="categoria">Categoria</label>
    <select v-model="categoria" id="categoria">
    <option value="">Seleccione una categoría</option>
    <option value="Electrónica">Electrónica</option>
    <option value="Indumentaria">Indumentaria</option>
    <option value="Hogar">Hogar</option>
    <option value="Deportes">Deportes</option>
    <option value="Alimentos">Alimentos</option>
    </select>

    <button type="submit">Enviar</button>
</form>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['agregar'])
const nombre = ref('')
const precio = ref(0)
const stock = ref(0)
const categoria = ref('')

function enviar() {
    if (nombre.value === '') {
        alert('El nombre es requerido')
        return
    }
    if (precio.value === 0) {
        alert('El precio es requerido')
        return
    }
    if (stock.value === 0){
        alert('El stock es requerido')
        return
    }
    if (categoria.value === ''){
        alert('La categoría es requerida')
        return
    }
    emit('agregar', { nombre: nombre.value, precio: precio.value, stock: stock.value, categoria: categoria.value })
    nombre.value = ''
    precio.value = 0
    stock.value = 0
    categoria.value = ''
}
</script>

<style>
</style>