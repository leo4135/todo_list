<template>
  <div>
    <div>
      <button
          @click="showPost"
      >добавить пост
      </button>
      <my-selected
          v-model="isSelected"
          :options="selectedSort"
      ></my-selected>
    </div>
    <my-dialog v-model:show="isVisible">
      <post-form
          @addPosts="addPost"
      />
    </my-dialog>
    <div v-if="!isLoading">
      <post-list
          :posts="posts"
          @delete="deletePosts"
      />
    </div>
    <div v-else>Идет загрузка</div>
  </div>
</template>

<script>
import PostList from "@/components/PostList";
import PostForm from "@/components/PostForm";
import MyDialog from "@/components/UI/MyDialog";
import axios from 'axios'
import MySelected from "@/components/UI/MySelected";

export default {
  components: {MySelected, MyDialog, PostForm, PostList},
  data() {
    return {
      posts: [],
      isVisible: false,
      isLoading: true,
      isSelected: '',
      selectedSort: [
        {value: 'title', name: 'по названию'},
        {value: 'body', name: 'по описанию'}
      ]
    }
  },
  methods: {
    addPost(post) {
      this.posts.push(post)
      this.isVisible = false
    },
    deletePosts(post) {
      this.posts = this.posts.filter(p => p.id != post.id)
    },
    showPost() {
      this.isVisible = true
    },
    fetchPosts() {
      setTimeout(async () => {
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.posts = response.data
        this.isLoading = false
      }, 1000)
    }
  },
  mounted() {
    this.fetchPosts()
  },
  watch: {
    isSelected(newValue) {
      this.posts.sort((post1, post2) => {
      return post1[newValue]?.localeCompare(post2[newValue])
      })
    }
  }
}
</script>

<style scoped>

</style>