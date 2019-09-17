<template>
  <div class="home">
    <AddPost v-on:add-post="addPost" />
    <PostList v-on:del-post="deletePost" v-bind:posts="posts" />
  </div>
</template>

<script>
import axios from "axios";

import PostList from "@/views/PostList.vue";
import AddPost from "@/views/AddPost.vue";

export default {
  name: 'home',
  components: {
    AddPost,
    PostList
  },
  data() {
    return {
      posts: [],
      errors: []
    };
  },
  methods: {
    addPost(newPost){
      const {title, body} = newPost;
      axios
      .post("https://jsonplaceholder.typicode.com/posts", {
        title: title,
        body: body
      })
      // making copy and not replacing data
      .then( res => (this.posts = [...this.posts, res.data]))
      .catch(err => console.log(err))
    },

    deletePost(id){
      axios.delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
      .then(res =>{
        this.posts = this.posts.filter(post => post.id !== id)
      })
      .catch(err =>{
        console.log(err)
      })
    }
  },
  created(){
    axios
    .get(`https://jsonplaceholder.typicode.com/posts?_limit=5`)
    .then(res => {
      this.posts = res.data
    })
    .catch(e =>{
      this.errors.push(e)
    });
  }
};
</script>
