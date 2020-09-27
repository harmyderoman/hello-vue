<template>
  <div>
    <img :src="imgUrl" alt="cat pic" />
    <h1>{{ catName }}</h1>
    <p>{{ text }}</p>
    <p>{{ website }}</p>
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
  border: 1px solid #cecece;
}
p {
  word-wrap: normal;
}
</style>
