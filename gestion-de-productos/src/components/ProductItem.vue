<script setup>
defineProps(['prod'])
defineEmits(['on-borrar'])
</script>

<template>
    <tr>
        <td>{{ prod.id }}</td>
        <td>{{ prod.nombre }}</td>
        <td>{{ prod.categoria }}</td>
        <td>{{ prod.precio }}</td>
        <td>{{ prod.stock }}</td>
        <td><button @click="$emit('on-borrar', prod.id)" class="btn-del">Eliminar</button></td>
    </tr>
    

</template>

<style scoped>
td{
    border: 1px solid black;
    padding: 10px;
    text-align: left;
}
.btn-del {
    background: #ff4d4d;
    color: white;
    border: none;
    padding: 5px 10px;
    border-radius: 4px;
    cursor: pointer;
}
</style>