<template>
  <div class="allFilters" v-if="this.$store.state.filter.length !== 0">
    <div class="filters">
      <div v-for="filter in this.$store.state.filter" :key="filter" class="filter">
        <div class="title">
          {{ filter}}
        </div>
        <div class="cancel" @click="clearFilter(filter)">
          <i class="fa-solid fa-xmark"></i>
        </div>
      </div>
    </div>
    <span class="clear" @click="clear()">Clear</span>
  </div>
</template>

<script>
export default {
  name: "Filter",
  methods: {
    clearFilter(filter) {
      const index = this.$store.state.filter.indexOf(filter);
      if (index !== -1) {
        this.$store.state.filter.splice(index, 1);
      }
    },
    clear() {
      this.$store.state.filter = [];
    }
  }
}
</script>

<style scoped lang="scss">
@import "../../scss/variables";
.allFilters {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: white;
  padding: 30px;
  .filters {
    display: flex;
    flex-wrap: wrap;
  }
  .filter {
    margin-right: 20px;
    display: flex;
    margin-bottom: 20px;
    border-radius: 10px;
    .title {
      background-color: $color_secondary;
      padding: 10px;
      color: $color_primary;
      font-weight: bold;
      border-radius: 5px;
    }
    .cancel {
      display: flex;
      align-items: center;
      padding: 5px;
      background-color: $color_primary;
      i {
        color: white;
        font-size: 15px;
        cursor: pointer;

      }
    }
  }
  .clear {
    color: gray;
    cursor: pointer;
  }
}


</style>