<template>
  <p>
    <input type="text" :value="value" @input="$emit('input', $event.target.value)">
    <c-component :value="value" v-on="$listeners"></c-component>
  </p>

</template>

<script>
    import CComponent from "@/components/CComponent";
    export default {
        name: "BComponent",
        props: [
          'value'
        ],
        components: {
          CComponent
        },
        methods: {

        },
        mounted() {
          console.log(this.$listeners, 'BComponent this.$listeners')
        }
    }
</script>

<style scoped>

</style>