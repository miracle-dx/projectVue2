<template>
  <div>i am noPropsAtribute</div>
  <!-- 一个非 prop 的 attribute 是指传向一个组件，但是该组件并没有相应 prop 定义的 attribute。那么这些 attribute 会被添加到这个组件的根元素上。 -->
</template>

<script>
export default {
    name: 'NoPropsAttribute',
    // 如果你不希望子组件的根元素继承 attribute，你可以在组件的选项中设置 inheritAttrs: false。
    // 注意 inheritAttrs: false 选项不会影响 style 和 class 的绑定。
    inheritAttrs: false,
}
</script>

<style>

</style>