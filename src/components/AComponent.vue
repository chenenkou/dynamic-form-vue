<template>
  <b-component :value="value" v-bind="$attrs" v-on="$listeners"></b-component>
</template>

<script>
import BComponent from "@/components/BComponent";
export default {
  name: "AComponent",
  props: [
      'value'
  ],
  components: {
    BComponent
  },
  methods: {

  }
}
</script>

<style scoped>

</style>