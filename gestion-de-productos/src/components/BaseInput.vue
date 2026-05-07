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
    margin-left: auto;
    margin-right: auto;
    width: 300px;
    text-align: center;
    padding: 5px 10px;
    border-radius: 30px;
    color: white;
    background-color: rgb(107, 6, 107);
}
</style>