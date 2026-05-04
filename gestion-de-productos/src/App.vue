<script setup>
import { ref, computed } from 'vue';
import ProductForm from './components/ProductForm.vue';
import ProductList from './components/ProductList.vue';

const productos = ref([])
const id = ref(1)
const cantidad_prod = computed(() => {
  return productos.value.reduce((total, p) => total + p.stock, 0);
});
const valor_inventario = computed(() => {
  return productos.value.reduce((total, p) => total + (p.stock * p.precio), 0);
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
  <div class="container">
    <div class="panel-carga">
      <ProductForm @on-agregar="agregarProducto" />
      <div class="resumen">
        <p>Cantidad de productos {{ cantidad_prod }}</p>
        <p>Valor del inventario ${{ valor_inventario }}</p>
      </div>
    </div>
    <div class="panel-productos">
      <ProductList :productos="productos" @on-eliminar="eliminarProducto" />
    </div>
  </div>


</template>
<style>
html,
body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background-color: rgb(27, 1, 27);
}

.container {
  display: flex;
  color: white;
}

.panel-productos {
  border: solid rgb(156, 10, 156);
  background-color: rgb(49, 2, 49);
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 5%;
  margin-left: 7%;
  width: 55%;
  height: 80vh;
  font-family: sans-serif;
}

.panel-carga {
  border: solid rgb(156, 10, 156);
  background-color: rgb(49, 2, 49);
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 5%;
  margin-left: 70px;
  width: 30%;
  font-family: sans-serif;
}
.resumen{
  margin-top: auto;
  border-top: solid rgb(156, 10, 156);
  text-align: center;
  width: 100%;
  box-sizing: border-box;
  padding: 20px 0;
}
p{
  margin-top: auto;
  padding-top: 5%;
}
</style>