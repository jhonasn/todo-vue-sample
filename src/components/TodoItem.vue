<template lang="html">
  <li :class="{ completed: todo.checked }">
    <input
    type="checkbox"
    v-model="todo.checked"
    :title="`${todo.checked ? 'un' : ''}complete todo ${todo.text} (${todo.id})`" />
    {{ todo.text }}
    <button type="button" @click="$emit('removed', todo.id)" :title="`delete todo ${todo.id}`">x</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
}
</script>

<style lang="css" scoped>
  li {
    display: block;
    text-align: left;
  }
  li.completed {
    text-decoration: line-through;
  }
</style>
