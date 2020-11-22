<template>
    <div>
        <button v-on:click="addCount">add</button>
        <p>count: {{count}}</p>
    </div>
</template>

<script>
export default {
    name: 'InjectionGrandson',
    inject: ['addCount'],
    props: {
        count: Number
    }
}
</script>

<style>

</style>