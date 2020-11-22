<template>
  <div>
      <div>count: {{count}}</div>
      <InjectionChild></InjectionChild>
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