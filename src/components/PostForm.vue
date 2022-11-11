<template>
  <form  @submit.prevent>
    <h4>Создание поста</h4>
    <input
        v-model="post.body"
        class="input"
        type="text"
        placeholder="Описание"
    />
    <button
        class="btn"
        @click="createPost"
    >
      Создать
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: '',
      }
    }
  },
  methods:{
    createPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        body: '',
      }
    }
  }
}
</script>

<style scoped>
form {
  max-width: 900px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;

}

.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}

.btn {
  align-self: flex-end;
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>