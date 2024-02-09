<script >
import MyButton from './UI/MyButton.vue';
import MyInput from './UI/MyInput.vue';

export default {
  components: { MyInput, MyButton },

  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.$emit("create", this.post),
        (this.post.id = Date.now()),
        (this.post = {
          title: "",
          body: "",
        });
    },
  },
};
</script>


<template>
  <form @submit.prevent class="form">
    <h4>Создание поста</h4>
    <my-input
      v-model="post.title"
      class="input"
      type="text"
      placeholder="Название"
    />
    <my-input
      v-model="post.body"
      class="input"
      type="text"
      placeholder="Описание"
    />
    <my-button class="btn2" @click="createPost">Создать</my-button>
  </form>
</template>


<style scoped>


.btn2{
    background: green;
}

.form {
  display: flex;
  flex-direction: column;
}
</style>