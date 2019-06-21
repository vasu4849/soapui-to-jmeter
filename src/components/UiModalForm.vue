<template>
  <div class="uimodal-form">
    <h1 v-if="!Object.keys(result).length">Please wait while we submit your data...</h1>
    <h1 v-else-if="Object.keys(result).length">{{result}}</h1>
    <div class="button" @click="closeModal()">Ok</div>
  </div>
</template>

<script>
export default {
  props: {
    result: Object
  },
  methods: {
    closeModal () {
      this.$emit('close')
    }
  }
}
</script>

<style scoped>

</style>
