<script >
import PostItem from "./PostItem.vue";
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>
<template>
  <div v-if="posts.length > 0">
    <h3>Список постов</h3>
    <post-item
      class="post"
      v-for="post in posts"
      :post="post"
      :key="post.id + 'r'"
      @remove="$emit('remove', post)"
    />
  </div>
  <div v-else class="postNoneBlock">
    <h2 class="postNone">Постов нет!!!</h2>
  </div>
</template>

<style scoped>
.postNoneBlock {
  display: flex;
  justify-content: center;
  margin-top: 50px;
}
</style>