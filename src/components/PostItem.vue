<template>
  <div class="post">
      <div ref="myReference" class="postBody">{{ post.body }}</div>
    <div>
      <button
          @click="$emit('remove',post)"
          >
          Удалить</button>
    </div>
  </div>
</template>



<script>
import { ref, onMounted } from "vue";
export default {
  setup() {
    const myReference = ref(null);
    const consoleHeight = () => {
      console.log(myReference.value.offsetHeight)
    }
    onMounted(() => {
      consoleHeight()
    })
    return{
      myReference
    }
  },
  props:{
    post:{
      type:Object,
      required:true,
    }
  },
}

</script>




<style scoped>
.post {
  padding: 50px 30px;
  margin-top: 15px;
  border: 1px solid #E8E6E6;
  box-shadow: 0px 0px 12px rgba(83, 83, 89, 0.12);
  border-radius: 16px;
  display: flex;
  align-self: center;
  justify-content: space-between;
  max-height: 435px;

}
.postBody{
  width: 800px;
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
}
</style>