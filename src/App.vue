<template>
  <div class="container">
    <Card
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
import { ref, onMounted } from "vue";
import Card from "./components/Card";

export default {
  name: "App",
  components: { Card },
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
    onMounted(fetchCats);
    return {
      cats,
    };
  },
};
</script>

<style>
body {
  background: #ecf0f3;
}
.container {
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-content: space-around;
  flex-wrap: wrap;
  padding: 30px 0px;
}
</style>
