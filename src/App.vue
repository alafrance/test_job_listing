<template>
  <Header />
  <Filter />
  <ListJob />
</template>

<script>
import Header from './components/Header.vue'
import ListJob from "./components/ListJob";
import Filter from "./components/Filter";

export default {
  name: 'App',
  components: {
    Filter,
    ListJob,
    Header
  }
}
</script>

<style lang="scss">
@import "../scss/variables.scss";
body {
  margin: 0;
  font-family: 'League Spartan', sans-serif;
  font-size: 13px;
  background-color: $color-accent;
}
</style>
