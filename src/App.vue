<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/index.png" />

    <Index msg="Here is the homepage of this site." />
  </div>
</template>

<script>
import Index from "./components/Index.vue";

export default {
  name: "App",
  components: {
    Index,
  },
};
</script>
