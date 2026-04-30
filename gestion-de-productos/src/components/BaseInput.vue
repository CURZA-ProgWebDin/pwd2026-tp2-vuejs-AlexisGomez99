<script setup>
    const value = defineModel();
    defineProps({
        tipo:{type: String, default: "text"},
        placeholder: String
    })
</script>

<template>
  <input :type="tipo" :placeholder="placeholder" v-model="value" class="input-field" />
</template>

<style scoped>
input{
    margin-left: 50px;
    margin-right: 50px;
    width: 400px;
    border-radius: 30px;
}
</style>