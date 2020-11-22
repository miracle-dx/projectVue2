<template>
  <div>
      <div>props验证，type限定prop类型，required限定是否必填，default提供默认值{{propA}}</div>
      <div>props验证，对象或数组默认值必须从一个工厂函数获取{{propB}}</div>
      <div>props验证, 可以通过validator自定义验证规格{{propC}}</div>
  </div>
</template>

<script>
export default {
    name: 'PropValidator',
    props: {
        propA: {
            type: String,
            required: true,
            default: 'i am a default string prop'
        },
        propB: {
            type: [Array],
            required: false,
            default: () => {
                return ['default arr']
            }
        },
        propC: {
            validator: (value) => {
                return [1,2,3].indexOf(value) !== -1
            }
        }
    }
}
</script>

<style>

</style>