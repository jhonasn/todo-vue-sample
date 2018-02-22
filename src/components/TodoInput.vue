<template>
  <div>
    <input type="text"
      :value="value"
      @input="$emit('input', $event.target.value)"
      @keydown.enter="$emit('added')" />
    <button type="button"
      @click="$emit('added')">
      +
    </button>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="css" scoped>
</style>
