<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <div class="app__btns">
      <my-button class="btnForm" @click="showDialog">Создать пост</my-button>
      <my-select v-model="selectedSort" :options="sortOptions"/>
    </div>

    <my-dialog v-model:show="dialogVisible"><post-form @create="createPost"/></my-dialog>

    <post-list :posts="posts" @remove="removePost" v-if="!isPostLoading" />
    <div v-else>Идет загрузка...</div>
  </div>
</template>





<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyDialog from "./components/UI/MyDialog.vue";
import MyButton from "./components/UI/MyButton.vue";
import axios from "axios";
import MySelect from "./components/UI/MySelect.vue";
export default {
  components: {
    PostList,
    PostForm,
    MyDialog,
    MyButton,
    MySelect,
  },

  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostLoading: false,
      selectedSort: "",
      sortOptions: [
        { value: "title", name: "По названию" },
        { value: "body", name: "По содержимому" },
      ],
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostLoading = true;
        setTimeout(async () => {
          const response = await axios.get(
            "https://jsonplaceholder.typicode.com/posts?_limit=10"
          );
          this.posts = response.data;
          this.isPostLoading = false;
        }, 1000);
      } catch (e) {
        alert("ошибка");
      } finally {
      }
    },
  },
  mounted() {
    this.fetchPosts();
  },
};
</script>



<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 15px;
}
.btnForm {
  margin-top: 10px;
  margin-bottom: 10px;
}
.app__btns {
  display: flex;
  justify-content: space-between;
}
</style>
