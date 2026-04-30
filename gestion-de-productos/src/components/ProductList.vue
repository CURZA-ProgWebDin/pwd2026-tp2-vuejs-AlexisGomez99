<script setup>
import { ref, computed } from 'vue';
import ProductItem from './ProductItem.vue';

const props = defineProps(['productos']);
const emit = defineEmits(['on-eliminar']);
const filtro = ref('Todos');
const productosFiltrados = computed(() => {
    if (filtro.value === 'Todos')
        return props.productos;
    return props.productos.filter(p => p.categoria === filtro.value);
});
</script>

<template>
    <div class="list-container">
        <label>Filtrar por: </label>
        <select v-model="filtro">
            <option value="Todos">Todos</option>
            <option value="Ropa">Ropa</option>
            <option value="Electrónica">Electrónica</option>
            <option value="Hogar">Hogar</option>
            <option value="Deportes">Deportes</option>
            <option value="Arte">Arte</option>
        </select>
    </div>
    <div v-if="productosFiltrados.length > 0">
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>NOMBRE</th>
                    <th>CATEGORIA</th>
                    <th>PRECIO</th>
                    <th>STOCK</th>
                    <th>ACCION</th>
                </tr>
            </thead>
            <tbody>
                <ProductItem v-for="prod in productosFiltrados" :key="prod.id" :prod="prod"
                    @on-borrar="id => emit('on-eliminar', id)" />
            </tbody>

        </table>
    </div>
    <p v-else>No hay productos cargados.</p>
</template>

<style scoped>
.list-container {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    text-align: center;
}

select {
    appearance: none;
    background-color: #f0f0f0;
    border: 1px solid #ccc;
    border-radius: 8px;
    width: 400px;
    padding: 7px;
    font-size: 13px;
    cursor: pointer;
}

table {
    margin-top: 30px;
    border: 3px solid;
    border-color: rgb(156, 10, 156);
    border-collapse: collapse;
    width: 100%;
}

th {
    border: 1px solid rgb(156, 10, 156);
    padding: 50px;
    text-align: left;
}
</style>