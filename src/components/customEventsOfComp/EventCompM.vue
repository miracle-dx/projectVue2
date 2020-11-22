<template>
  <div>
      <input
        type="text"
        v-on:input = "$emit('input',$event.target.value)"
        v-bind:value = "value"
      >
  </div>
</template>

<script>
export default {
    name: 'EventCompM',
    props: {
      value: String
    }
}
</script>

<style>

</style>