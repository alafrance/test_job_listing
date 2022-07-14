<template>
  <div>
    <p>Coucou</p>
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

</style>