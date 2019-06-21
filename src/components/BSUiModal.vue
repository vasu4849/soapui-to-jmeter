<template>
  <div>
    <b-modal v-model="active" id="modal-center" centered title="status">
      <p v-if="errors.length" class="my-4">{{errors}}</p>
      <p v-else-if="!Object.keys(result).length" class="my-4">Processing your request..
        <b-spinner lable="Spinning"></b-spinner>
      </p>
      <p v-else-if="Object.keys(result).length" class="my-4" centered>{{result}}</p>
      <template slot="modal-footer">
        <b-button @click="closeModal()" class="btn-center">OK</b-button>
      </template>
    </b-modal>
</div>
</template>

<script>
export default {
  props: {
    active: Boolean,
    cancellable: [Number, Boolean],
    result: Object,
    errors: Array
  },
  methods: {
    closeModal () {
      this.$emit('close')
    }
  }
}
</script>

<style scoped>
.btn-center{
  margin-right: 46%;
}
</style>
