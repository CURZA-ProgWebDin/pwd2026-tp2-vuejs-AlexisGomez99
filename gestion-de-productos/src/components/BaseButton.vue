<script setup>
defineProps({tipo:{type:String}})
</script>

<template>
    <button type="tipo">
        <slot>
            ENVIAR
        </slot>
    </button>
</template>

