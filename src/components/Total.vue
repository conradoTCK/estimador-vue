<template>
  <input type="text" v-bind:value="total">
</template>

<script>
export default {
  name: 'Total',
  props: {
    total: String
  },
  methods: {
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
