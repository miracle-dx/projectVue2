<template>
  <div>
      <button v-on:click="sendMesage">emit</button>
  </div>
</template>

<script>
import { EventBus } from '../../Bus.js';
export default {
    name: 'EventBusCompA',
    methods: {
        sendMesage() {
            EventBus.$emit('sendM','the message from page A')
        }
    },
    beforeDestory() {
        EventBus.$off('sendM')
    }

}
</script>

<style>

</style>