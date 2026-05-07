<script setup>
import { ref, computed } from 'vue';
import ProductForm from './components/ProductForm.vue';
import ProductList from './components/ProductList.vue';
import AppLayout from './components/Layouts/AppLayout.vue';
import HeaderComponent from './components/HeaderComponent.vue';
import AsideComponent from './components/AsideComponent.vue';
const components = {
  Carga: ProductForm,
  Inventario: ProductList
};

const vistaActual = ref('Carga');
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
  <AppLayout>
    <template #header>
      <HeaderComponent>
        <div class="resumen">
          <p>Cantidad de productos {{ cantidad_prod }}</p>
          <p>Valor del inventario ${{ valor_inventario }}</p>
        </div>
      </HeaderComponent>
    </template>
    <template #menu_lateral>
      <AsideComponent>
        <div class="menu"> <!-- Esto no se si esta bien que quede directamente en App o si hay alguna forma de hacerlo en AsideComponent -->
          <nav class="nav-interna">
            <button @click="vistaActual = 'Carga'">Nueva Carga</button>
            <button @click="vistaActual = 'Inventario'">Ver Lista</button>
          </nav>
        </div>
      </AsideComponent>
    </template>
    <template #main>
      <div class="container">
        <keep-alive>
          <component :is="components[vistaActual]" :productos="productos" @on-agregar="agregarProducto"
            @on-eliminar="eliminarProducto" />
        </keep-alive>
      </div>
    </template>
  </AppLayout>
</template>
<style>
html,
body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background-color: rgb(26, 1, 31);
}

.container {
  display: flex;
  flex-direction: column;
  text-align: center;
  color: white;
}
.nav-interna{
  margin-bottom: 2%;
}
button {
  margin-top: 10px;
  background: #7a0791;
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 4px;
  cursor: pointer;
}
</style>