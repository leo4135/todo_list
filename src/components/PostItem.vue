<template>
  <div>
    <div>Название: {{ post.title }}</div>
    <div>Название: {{ post.body }}</div>
    <button @click="$emit('delete', post)">Удалить</button>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object
    }
  }
}
</script>

<style scoped>

</style>