<template>
    <div>
        <InjectionGrandson  v-bind="$attrs"></InjectionGrandson>
        <div>attrs: {{attrString}}</div>
    </div>
</template>

<script>
import InjectionGrandson from "./InjectionGrandson";
export default {
    name: 'InjectionChild',
    components: {
        InjectionGrandson
    },
    props: {
        attrString: String
    }
}
</script>

<style>

</style>