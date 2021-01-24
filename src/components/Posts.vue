<template>
  <div>Posts test</div>
  <ul>
    <li v-for="post in posts" :key="post.id">{{ post.body }}</li>
    <li v-for="post in posts" :key="post.id">{{ post.id }}</li>
  </ul>
</template>



<script>
import axios from "axios";
import { onMounted, ref } from "vue";

export default {
  setup() {
    const posts = ref([]);

    const getPosts = async () => {
      let response = await axios.get(
        "https://jsonplaceholder.typicode.com/posts"
      );

      posts.value = response.data.slice(1.1);
    };

    onMounted(() => getPosts());

    return { posts };
  },
};
</script>
