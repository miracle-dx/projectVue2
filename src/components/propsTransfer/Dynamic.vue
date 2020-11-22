<template>
  <div>
       <div>父组件App传来的动态参数: {{message}}</div>
       <div>将props的初始值本地化: {{count}}</div>
       <div>props以原始值传入并通过computed计算属性进行转化：{{doubleCount}}</div>
  </div>
</template>

<script>
export default {
    name: 'Dynamic',
    props: ['message', 'obj', 'arr', 'id', 'context'],
    data() {
        return {
            count: this.message
        }
    },
    computed: {
        doubleCount: function() {
            return this.message * 2
        }
    },
    mounted() {
        // this指向Vue实例，this._props指向props对象,props被代理到了vue实例上，可以从this上直接获取
        console.info(this, this._props, this._props.message === this.message)
    }
}
</script>

<style>

</style>