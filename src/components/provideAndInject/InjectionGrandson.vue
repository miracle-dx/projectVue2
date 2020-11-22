<template>
    <button v-on:click="addCount">add</button>
</template>

<script>
export default {
    name: 'InjectionGrandson',
    inject: ['addCount']
}
</script>

<style>

</style>