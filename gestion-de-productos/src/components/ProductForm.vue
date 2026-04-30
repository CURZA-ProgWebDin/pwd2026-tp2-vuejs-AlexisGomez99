<script setup>
import { ref } from 'vue';
import BaseInput from './BaseInput.vue';
import BaseButton from './BaseButton.vue';
const formulario = ref({
    'nombre': "",
    'precio': null,
    'stock': null,
    'categoria': ""
});

const emit = defineEmits(['on-agregar']);

function manejarEnvio() {
    if (formulario.value.nombre === '' || formulario.value.categoria === '' || formulario.value.precio <= 0 || formulario.value.stock <= 0) {
        alert("Complete los campos correctamente.");
        return;
    }
    emit('on-agregar', { ...formulario.value });

    formulario.value = {
        'nombre': "",
        'precio': null,
        'stock': null,
        'categoria': ""
    };
}
</script>

<template>
    <form @submit.prevent="manejarEnvio" class="form-prod">
        <h3>Nuevo Producto</h3>
        <label for="nombre">Nombre:</label>
        <BaseInput v-model="formulario.nombre"/>
        <label for="precio">Precio:</label>
        <BaseInput tipo="number" v-model.number="formulario.precio"/>
        <label for="stock">Stock:</label>
        <BaseInput tipo="number" v-model.number="formulario.stock"/>
        <div class="base-input">
            <label>Categoría</label>
            <select v-model="formulario.categoria">
                <option value="" disabled>Seleccione...</option>
                <option value="Electrónica">Electrónica</option>
                <option value="Hogar">Hogar</option>
                <option value="Ropa">Ropa</option>
                <option value="Deportes">Deportes</option>
                <option value="Arte">Arte</option>
            </select>
        </div>

        <BaseButton tipo="submit" >Guardar Producto</BaseButton>
    </form>
</template>

<style scoped>
.form-prod{
    align-items: center;
    display: flex;
    flex-direction: column;
    margin-left: auto;
    margin-right: auto;
    height: 300px;
}
.base-input{
    display: flex;
    flex-direction: column;
}

button{
    margin-top: 10px;
    background: #4d68ff;
    color: white;
    border: none;
    padding: 5px 10px;
    border-radius: 4px;
    cursor: pointer;
}
</style>
