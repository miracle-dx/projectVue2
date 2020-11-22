<template>
  <div>
       <input
            type="text"
            v-on="inputListeners"
            v-bind:value="value"
        >
  </div>
</template>

<script>
export default {
    name: 'EventCompL',
    props: {
        value: String
    },
    computed: {
        inputListeners: function() {
            return Object.assign({},
            this.$listeners,
            {
                input: (e) => {
                    this.$emit('input',e.target.value)
                }
            }
            )
        }
    }
    // mounted() {
    //     console.info(this.$listeners)
    // }
    // $listeners为对象结构，key是原生事件名称，value位父组件中定义的事件处理函数

}
</script>

<style>

</style>