<template>
  <form @click="focusField" @submit.prevent>
    <div class="textarea__container">
      <div class="header__textarea">
        <div class="textarea__img">
          <img src="../img/buildHomeAvatar.svg" alt="">
        </div>
        <textarea
            v-model="post.body"
            class="textArea"
            @input="lenghtCalc"
            type="text"
            :style="textareaStyle"
            placeholder="Создайте новый пост"
            :maxlength='maxlength'
        />
      </div>
      <div class="counter__simbol">{{ counterSumbol }}</div>
      <div class="control__panel" v-if="showPanel">
        <button
            class="btn"
            @click="createPost"
        >
          Опубликовать
        </button>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  props:{
    showPanel:{
      type: Boolean,
      required: true,
    }
  },
  inheritAttrs: false,
  data() {
    return {
      post: {
        body: '',
      },
      counterSumbol: 1000,
      maxlength: 1000,
      textareaHeight: 59,
    }
  },
  computed: {
    textareaStyle() {
      return {
        height: `${this.textareaHeight}px`
      }
    }
  },
  methods: {
    focusField() {
      this.$emit('showControlPanel', true)
    },

    createPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        body: '',
      }
      this.textareaHeight = 59
      this.$emit('closeControlPanel', false)
    },
    lenghtCalc(e) {
      computed: {
        this.textareaHeight = e.target.scrollHeight
        this.counterSumbol = 1000 - e.target.value.length
      }
    }
  },

}
</script>

<style scoped>
.counter__simbol {
  justify-content: flex-end;
  padding: 0 20px 7px 0;
  display: flex;
  align-items: flex-end;
  font-weight: 400;
  font-size: 12px;
  line-height: 14px;
  color: #94A2B3;
  background: #FFFFFF;
}

.header__textarea {
  min-height: 80px;
  display: flex;
  background: #FFFFFF;
  border-radius: 16px;
}

.control__panel {
  height: 70px;
  max-width: 100%;
  width: 100%;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding: 0 20px 0 20px;
  border-radius: 0 0 16px 16px;
  background: #FFFFFF;
  border-top: 1px solid #E8E6E6;
}

form {
  max-width: 900px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;

}

.textarea__container {
  display: flex;
  box-shadow: 0px 0px 12px rgba(83, 83, 89, 0.12);
  border: 1px solid #E8E6E6;
  background: #FFFFFF;
  flex-direction: column;
  border-radius: 16px;
}

.textArea {
  resize: none;
  font-style: normal;
  font-weight: 400;
  font-size: 15px;
  line-height: 24px;
  color: #C1C3CA;
  max-width: 768px;
  width: 100%;
  border: none;
  min-height: 59px;
  background: #FFFFFF;
  padding: 20px 20px 0px 20px;
  max-height: 216px;
  height: auto;
}

.textArea::-webkit-scrollbar {
  width: 0;
}

.textArea:focus {
  color: #18191F;
  font-style: normal;
  font-weight: 400;
  font-size: 15px;
  line-height: 24px;
  width: 100%;
  min-height: 80px;
  background: #FFFFFF;
  outline: none;
}

.btn {
  border: none;
  background: #43A5D2;
  border-radius: 10px;
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  color: #FFFFFF;
  max-width: 147px;
  width: 100%;
  max-height: 40px;
  height: 100%;
}

.textarea__img {
  max-height: 100%;
  margin: 20px 20px 0 20px;
  background: #FFFFFF;
}

.textarea__img img {
  max-width: 40px;
  max-height: 40px;
  width: 100%;
  height: 100%;

}
</style>