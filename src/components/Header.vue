<template>
  <div class="header">
    <img src="@/assets/bg-header-mobile.svg" alt="Header Background" class="">
  </div>
</template>

<script>
import {store} from "../store.js";
export default {
  name: "Header",
  mounted() {
    console.log(store.state.count);
  }
}
</script>

<style scoped lang="scss">
@import "../../scss/variables";

.header {
  img {
    width: 100vw;
    height: 100pxg;
  }
  background-color: $color_primary;
}
</style>