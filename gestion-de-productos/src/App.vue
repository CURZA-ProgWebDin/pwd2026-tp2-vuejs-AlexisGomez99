<script setup>
import { ref, computed } from 'vue';
import ProductForm from './components/ProductForm.vue';
import ProductList from './components/ProductList.vue';

const productos = ref([])
const id = ref(1)
const cantidad_prod = computed(() =>{
  return productos.value.reduce((total,p) => total + p.stock,0);
});
const valor_inventario = computed(() =>{
  return productos.value.reduce((total,p) => total + (p.stock * p.precio),0);
});

function agregarProducto(nuevo) {
  const producto = { ...nuevo, 'id': id.value };
  id.value++;
  productos.value.push(producto);
}

const eliminarProducto = (id) => {
  productos.value = productos.value.filter(p => p.id !== id);
};
</script>

<template>
  <div class="app">
    <p>Cantidad de productos {{ cantidad_prod }}</p>
    <p>Valor del inventario {{ valor_inventario }}</p>
    <ProductForm @on-agregar="agregarProducto" />
    <ProductList :productos="productos" @on-eliminar="eliminarProducto" />
  </div>

</template>
<style>
html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background-color: rgb(61, 6, 61); 
}
.app {
  background-color: rgb(49, 2, 49);
  display: flex;
  flex-direction: column;
  align-items: center;
  color: white;
  margin-left: 20%;
  margin-right: 20%;
  height: 100vh;
  font-family: sans-serif;
}
</style>