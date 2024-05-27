<script setup lang="ts">
defineProps<{ msg: string }>()
</script>

<template>
 <h1>{{msg}}</h1>
</template>

<style scoped>
h1{
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgb(124, 122, 122)

}
</style>
