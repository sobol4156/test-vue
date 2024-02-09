<template>
  <div class="post">
    <div>
      <div><strong>Название:</strong> {{ post.title }}</div>
      <div><strong>Описание:</strong>{{ post.body }}</div>
    </div>
    <div class="post__btns">
        <my-button @click="$emit('remove', post)" class="btn1">Удалить</my-button>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style  scoped>
.post {
  padding: 15px;
  border: 2px solid black;
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.btn1{
    background: rgb(94, 39, 39);
}
.btn1:hover{
    background: rgb(58, 25, 25);
    transform: rotate(0deg) scale(1.05);

}
</style>