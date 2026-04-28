<script setup>
import { ref } from 'vue';
const product = ref({
    'id': 0,
    'nombre': "",
    'precio': 0,
    'stock': 0,
    'categoria': ""
});

const agregarDatos = () => {
    console.log(product)
}
</script>

<template>
    <div class="form">
        <label for="nombre">Nombre:</label>
        <input v-model="product.nombre" type="text">
        <label for="precio">Precio:</label>
        <input v-model="product.precio" type="numbre">
        <label for="stock">Stock:</label>
        <input v-model="product.stock" type="numbre">
        <label for="categoria">Categoria:</label>
        <input v-model="product.categoria" type="text">
        <button @click="agregarDatos">Agregar</button>
    </div>
</template>

<style>
.form {
    width: 100%;
    max-width: 400px;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 100px;
    margin: auto;
    background-color: black;
    color: aqua;
}

input {
    width: 320px;
    align-items: left;
    box-sizing: border-box;
}

button {
    color: black;
    margin-top: 50px;
}
</style>