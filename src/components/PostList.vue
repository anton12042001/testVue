<template>
  <div class="postList">
    <h3>Список постов</h3>
    <post-item

        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove',post)"
    />
  </div>
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
  margin: 0 auto;
  max-width: 900px;
}

</style>