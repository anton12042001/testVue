<template>
  <div class="app">
    <post-form
        @create="createPost"
    />
    <post-list
        :posts="posts"
        @remove="removePost"
    />
  </div>
</template>


<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";

export default {
  components: {
    PostList, PostForm
  },
  data() {
    return {
      posts: [
        {id: 1, body: "Описание поста"},
        {id: 2, body: "Описание поста 2"},
        {id: 3, body: "Описание поста 3"},
        {id: 4, body: "Описание поста 4"},
      ],
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post)
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    }
  }
}
</script>


<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;
}

.app {
  background: #F8F8F8;
  height: 100vh;
  padding: 60px;
}


</style>