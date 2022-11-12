<template>
  <form @submit.prevent>
    <div class="textarea__container">
      <div class="textarea__img">
        <img src="../img/buildHomeAvatar.svg" alt="">
      </div>
      <textarea
          v-model="post.body"
          class="textArea"
          @input="lenghtCalc"
          type="text"
          placeholder="Создайте новый пост"
      />
    </div>
    <button
        class="btn"
        @click="createPost"
    >
      Создать
    </button>
  </form>
  <div>Осталось {{counterSumbol}}</div>
</template>

<script>
export default {
  data() {
    return {
      post: {
        body: '',
      },
      counterSumbol:0,
      lastText:''
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        body: '',
      }
    },
    lenghtCalc(e) {
      if(this.counterSumbol === 1){
        this.lastText = e.target.value
        this.body = this.lastText
      }
      if(this.counterSumbol < 0){
        this.body = this.lastText
      }
      computed: {
        this.counterSumbol = 5 -  e.target.value.length
      }
    }
  },

}
</script>

<style scoped>
form {
  max-width: 900px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;

}

.textarea__container {
  display: flex;
  box-shadow: 0px 0px 12px rgba(83, 83, 89, 0.12);
  border-radius: 16px;
  border: 1px solid #E8E6E6;
  background: #FFFFFF;
}

.textArea {
  resize: none;
  font-style: normal;
  font-weight: 400;
  font-size: 15px;
  line-height: 24px;
  color: #C1C3CA;
  max-width: 758px;
  width: 100%;
  border: none;
  border-radius: 16px;
  height: 80px;
  background: #FFFFFF;
  padding: 0 20px 0 20px;

}

.textArea:focus {
  color: #18191F;
  font-style: normal;
  font-weight: 400;
  font-size: 15px;
  line-height: 24px;
  width: 100%;
  border-radius: 16px;
  height: 80px;
  background: #FFFFFF;
  outline: none;
}

.btn {
  align-self: flex-end;
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}

.textarea__img {
  display: flex;
  align-items: center;
  max-height: 100%;
  margin: 0 20px 0 20px;
  background: #FFFFFF;
}

.textarea__img img {
  max-width: 40px;
  max-height: 40px;
  width: 100%;
  height: 100%;

}
</style>