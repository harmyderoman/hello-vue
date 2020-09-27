<template>
  <div>
    <img :src="imgUrl" alt="cat pic" />
    <h1>{{ catName }}</h1>
    <p>
      <i>{{ text }}</i>
    </p>
    <p>
      <b>{{ website }}</b>
    </p>
  </div>
</template>

<script>
import { computed } from "vue";

export default {
  props: {
    id: String,
    name: String,
    text: String,
    website: String,
  },
  setup(props) {
    const imgUrl = computed(
      () => `https://robohash.org/${props.id}?set=set4&size=180x180`
    );
    const catName = computed(() => props.name.replace(/[_.-]/gi, " "));
    return {
      imgUrl,
      catName,
    };
  },
  computed: {
    //   imgUrl() {
    //     return `https://robohash.org/${this.id}?set=set4&size=180x180`;
    //   },
    // catName() {
    //   return this.name.replace(/[_.-]/gi, " ");
    // },
  },
};
</script>

<style scoped>
div {
  width: 400px;
  height: 380px;
  position: relative;
  background: #ecf0f3;
  margin-bottom: 30px;
  padding: 30px 5px;
  border-radius: 32px;
  text-align: center;
  cursor: pointer;
  font-family: "Montserrat", sans-serif;
  font-size: 22px;
  font-weight: semibold;
  box-shadow: -6px -6px 10px rgba(255, 255, 255, 0.8),
    6px 6px 10px rgba(0, 0, 0, 0.2);
  color: #6f6cde;
}
p {
  word-wrap: normal;
}
</style>
