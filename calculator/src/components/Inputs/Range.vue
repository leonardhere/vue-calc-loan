<template>
  <input class="input--range" type="range" :min="min" :max="max" :step="step" @input="handleInput">
</template>

<script>
export default {
  name: 'Range',
  props: {
    min: Number,
    max: Number,
    step: Number,
  },
  methods: {
    handleInput (event) {
      this.$emit('input', event.target.value)
    }
  }
}
</script>

<style scoped>

</style>
