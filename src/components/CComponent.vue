<template>
  <el-input :value="value" @input="(val) => $emit('input', val)"></el-input>
</template>

<script>
export default {
  name: "CComponent",
  props: [
    'value'
  ],
  mounted() {
    console.log(this.$listeners, 'CComponent this.$listeners')
  }
}
</script>

<style scoped>

</style>