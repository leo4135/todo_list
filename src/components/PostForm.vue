<template>
  <div class="input">
  <my-input
      v-model="post.title"
  />
  <my-input
      v-model="post.body"
  />
<button @click="addPost">Добавить</button>
  </div>
</template>

<script>
import MyInput from "@/components/UI/MyInput";
export default {
  components: {MyInput},
  data(){
    return{
      post: {
        id: Date.now(),
        title:'',
        body:''
      }
    }
  },
  methods:{
    addPost(){
      this.$emit('addPosts', this.post)
      this.post = {
        title: '',
        body: ''
      }
    }
  }
}
</script>

<style scoped>
.input {
  box-sizing: border-box;
  padding: 20px 20px;
  display: flex;
}
</style>