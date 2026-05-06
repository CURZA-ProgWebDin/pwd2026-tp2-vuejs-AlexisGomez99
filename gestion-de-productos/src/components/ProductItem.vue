<script setup>
const props = defineProps(['prod']);
const emit = defineEmits(['on-borrar']);

function eliminar(){
    console.log("se elimino el producto con id:" + props.prod.id);
    emit('on-borrar', props.prod.id);
}
</script>

<template>
    <tr>
        <td>{{ props.prod.id }}</td>
        <td>{{ props.prod.nombre }}</td>
        <td>{{ props.prod.categoria }}</td>
        <td>{{ props.prod.precio }}</td>
        <td>{{ props.prod.stock }}</td>
        <td><button @click="eliminar" class="btn-del">Eliminar</button></td>
    </tr>
</template>

<style scoped>
td{
    border: 1px solid rgb(156, 10, 156);
    padding: 10px;
    text-align: center;
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