<template>
    <div>{{msg}}</div>
</template>

<script>
import { EventBus } from '../../Bus.js';
export default {
    name: 'EventBusCompB',
    data() {
        return {
            msg: null
        }
    },
    mounted() {
        EventBus.$on('sendM',(msg) => {
            this.msg = msg
        })
    },
    beforeDestory() {
        EventBus.$off('sendM')
    }

}
</script>

<style>

</style>