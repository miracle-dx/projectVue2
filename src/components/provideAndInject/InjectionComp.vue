<template>
  <div>
      <div>count: {{count}}</div>
      <InjectionChild v-bind:count="count" v-bind="$attrs"></InjectionChild>
  </div>
</template>

<script>
import InjectionChild from "./InjectionChild";
export default {
    name: 'InjectionComp',
    data() {
        return {
            count: 0
        }
    },
    props: {
        attrs: String
    },
    methods: {
        addCount() {
            this.count ++
        }
    },
    provide: function() {
        return {
            addCount: this.addCount
        }
    },
    components: {
        InjectionChild
    }

}
</script>

<style>

</style>