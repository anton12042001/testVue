<template>
  <div class="post">
    <div class="header__delete_post" >
      <div class="header__img-title" >
        <div class="header__img" ><img src="../img/buildHomeAvatar.svg" alt=""></div>
        <div class="header__title">Строительство частных домов</div>
      </div>
      <div class="button__delete-post" >
        <button
            class="header__delete"
            @click="$emit('remove',post)"
        >
          Удалить
        </button>
      </div>
    </div>
    <div>
      <div :class="className">
        <div class="body__text" ref="myReference">{{ post.body }}</div>
      </div>
      <div class="button__more-info"  v-if="showButtonMoreInfo && !showMoreInfo">
        <button class="show__more_info" @click="getMoreInfo">Показать еще...</button>
      </div>
      <div class="button__more-info"  v-else-if="showButtonMoreInfo && showMoreInfo">
        <button class="show__more_info" @click="getMoreInfo">Скрыть</button>
      </div>
    </div>
  </div>

</template>


<script>
import {ref, onMounted, getCurrentInstance} from "vue";

export default {
  props: {
    post: {
      type: Object,
      required: true,
    }
  },
  data() {
    return {
      showButtonMoreInfo: false,
      showMoreInfo: false,
    }
  },
  computed: {
    className: function () {
      if (this.showMoreInfo === true) {
        return "post__body_full-content"
      } else {
        return "post__body"
      }
    }
  },
  methods: {
    getMoreInfo() {
      this.showMoreInfo = !this.showMoreInfo
    }
  },
  setup() {
    const myReference = ref(null);
    const consoleHeight = () => {
      if (myReference.value.offsetHeight === 168) {
        getCurrentInstance().data.showButtonMoreInfo = true
      }
    }
    onMounted(() => {
      consoleHeight()
    })
    return {
      myReference
    }
  },
}

</script>


<style scoped>
.header__delete{
  background: #FFFFFF;
  border: none;
  color: #C1C3CA;
  font-weight: 400;
  font-size: 15px;
  line-height: 24px;

}
.header__title{
  background: #FFFFFF;
  margin: 10px 0 0 0;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 20px;
  color: #18191F;
}
.header__img-title{
  background: #FFFFFF;
  display: flex;
}
.header__img{

  margin: 0 20px 24px 0;
}
.header__img img{
  max-width: 60px;
  max-height: 60px;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.show__more_info{
  font-weight: 400;
  font-size: 14px;
  line-height: 23px;
  color: #43A5D2;
  border:none;
  background: #FFFFFF;
}
.header__delete_post{
  display: flex;
  background: #FFFFFF;
  justify-content: space-between;
}
.post {
  max-width: 900px;
  width: 100%;
  padding: 30px 50px;
  margin-top: 15px;
  border: 1px solid #E8E6E6;
  box-shadow: 0px 0px 12px rgba(83, 83, 89, 0.12);
  border-radius: 16px;
  display: flex;
  align-self: center;
  justify-content: space-between;
  flex-direction: column;
  background: #FFFFFF;
}
.post__body {

  word-wrap: break-word;
  max-width: 800px;
  width: 100%;
  max-height: 168px;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 7;
  overflow: hidden;
  font-style: normal;
  font-weight: 400;
  font-size: 15px;
  line-height: 24px;
  color: #18191F;
  background: #FFFFFF;
}
.post__body_full-content {
  word-wrap: break-word;
  width: 800px;
  font-style: normal;
  font-weight: 400;
  font-size: 15px;
  line-height: 24px;
  color: #18191F;
  background: #FFFFFF;
}

.button__delete-post,
.button__more-info,
.body__text{
  background: #FFFFFF;
}

</style>