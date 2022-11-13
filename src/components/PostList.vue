<template>
  <div v-if="posts.length > 0" class="postList">
    <post-item
        v-for="post in posts.slice().reverse()"
        :post="post"
        :key="post.id"
        @remove="$emit('remove',post)"
    />
  </div>
  <h2 v-else >Список постов пуст</h2>
</template>

<script>
import PostItem from "@/components/PostItem";
export default {
  components: {PostItem},
  props:{
    posts:{
      type:Array,
      required:true,
    }
  }
}
</script>

<style scoped>
.postList{

  padding: 0 0 25px 0;
  margin: 0 auto;
  max-width: 900px;
}

</style>