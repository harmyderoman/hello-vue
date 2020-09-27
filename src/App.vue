<template>
  <h1>Vue 3</h1>
  <div class="container">
    <PostCard
      v-for="cat in cats"
      :id="cat.id"
      :name="cat.username"
      :text="cat.company.catchPhrase"
      :key="cat.id"
      :website="cat.website"
    />
  </div>
</template>

<script>
import { ref } from "vue";
import PostCard from "./components/PostCard";

export default {
  name: "App",
  components: { PostCard },
  data() {
    return {};
  },
  setup() {
    const cats = ref([]);
    const fetchCats = async () => {
      cats.value = await fetch(
        "https://jsonplaceholder.typicode.com/users"
      ).then((response) => response.json());
    };
    return {
      cats,
      fetchCats,
    };
  },
  mounted() {
    this.fetchCats();
  },
};
</script>

<style>
.container {
  height: 800px;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-content: space-around;
  flex-wrap: wrap;
  padding: 20px 100px;
}
</style>
