<script setup>

</script>

<template>
    <header>
        <slot name="header"></slot>
    </header>
    <aside>
        <slot name="menu_lateral"></slot>
    </aside>
    <main>
        <slot name="main"></slot>
    </main>
    <footer>
        <slot name="footer"></slot>
    </footer>
</template>

<style scoped>
aside{
    border: solid 2px;
    border-color: rgb(156, 10, 156);
    background-color: rgb(34, 2, 49);
    margin-left: 20%;
    margin-right: 20%;
    height: auto;
    width: auto;
}
main{
    border-bottom: solid 2px;
    border-left: solid 2px;
    border-right: solid 2px;
    border-color: rgb(156, 10, 156);
    background-color: rgb(60, 3, 87);
    margin-left: 20%;
    margin-right: 20%;
    height: auto;
    width: auto;
}

</style>