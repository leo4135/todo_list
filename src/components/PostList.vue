<template>
  <div v-if="posts.length > 0">
  <post-item
      @delete="$emit('delete', post)"
      :post="post"
      v-for="post in posts"
      :key="post.id">
  </post-item>
  </div>
  <div v-else> Нет постов </div>
</template>

<script>
import PostItem from "@/components/PostItem";
export default {
  components: {PostItem},
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>