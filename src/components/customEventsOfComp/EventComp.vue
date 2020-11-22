<template>
  <div>
      <input
        type="text"
        v-on:input = input
        v-bind:value = "value"
      >
  </div>
</template>

<script>
export default {
    name: 'EventComp',
    props: {
        value: Number
    },
    methods: {
        input(e) {
            // e代表的就是当前实例的$event对象
            // $emit触发change事件
            this.$emit('change',e.target.value)
        }
    }
}
</script>

<style>

</style>