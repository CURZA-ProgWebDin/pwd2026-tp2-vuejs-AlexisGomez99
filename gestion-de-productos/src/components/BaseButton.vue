<script setup>
defineProps({ tipo: { type: String } })
</script>

<template>
    <button type="tipo">
        <slot>
            ENVIAR
        </slot>
    </button>
</template>

<style scoped>
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