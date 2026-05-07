<script setup></script>

<template>
    
    <div class="container">
        <h1>STOCK DE PRODUCTOS</h1>
        <slot></slot>
    </div>
</template>

<style scoped>
.container{
    display: flex;
    flex-direction: column;
    box-sizing: border-box;
    text-align: center;
}

h1 {
    color: white;
}
</style>