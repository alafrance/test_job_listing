<template>
  <div class="job" v-if="haveFilter()" :key="this.$store.state.filter" :class="isNew && isFeatured ? 'borderLeft' : ''">
<!--    <img :src="require(image)" alt="Logo Job">-->
    <div class="title">
      <h1> {{ title }} </h1>
      <div v-if="isNew" class="new">New!</div>
      <div v-if="isFeatured" class="featured">featured</div>
    </div>
    <h2>{{jobName}}</h2>
    <div class="infos">
      <div v-for="(info, index) in infos" :key="info" class="info">
        {{ info }}
        <div v-if="index !== infos.length - 1" class="point"></div>
      </div>
    </div>

    <div class="line"></div>
    <div class="filters">
      <span v-for="role in roles" :key="role" class="filter" :data-role="role" @click="addFilter($event.currentTarget.getAttribute('data-role'))">
        {{ role }}
      </span>
      <span v-for="level in levels" :key="level" class="filter"  :data-level="level" @click="addFilter($event.currentTarget.getAttribute('data-level'))">
        {{ level }}
      </span>
      <span v-for="language in languages" :key="language" class="filter"  :data-languages="language" @click="addFilter($event.currentTarget.getAttribute('data-languages'))">
        {{ language }}

      </span>
      <span v-for="tool in tools" :key="tool" class="filter"  :data-tools="tool" @click="addFilter($event.currentTarget.getAttribute('data-tools'))">
        {{ tool }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Job",
  props: {
    image: String,
    title: String,
    jobName: String,
    infos: [String],
    roles: [String],
    levels: [String],
    isNew: Boolean,
    isFeatured: Boolean,
    languages: [String],
    tools: [String]
  },
  methods: {
    addFilter(attribute) {
      if (!this.$store.state.filter.includes(attribute)) {
        this.$store.state.filter.push(attribute)
      }
    },
    haveFilter() {
      if (this.$store.state.filter.length === 0) {
        return true;
      }
      for (const filter of this.$store.state.filter) {
        let is_includes = false;
        for (const role of this.roles) {
          if (filter.includes(role)) {
            is_includes = true;
          }
        }
        for (const level of this.levels) {
          if (filter.includes(level)) {
            is_includes = true;
          }
        }
        for (const language of this.languages) {
          if (filter.includes(language)) {
            is_includes = true;
          }
        }
        for (const tool of this.tools) {
          if (filter.includes(tool)) {
            is_includes = true;
          }
        }
        if (!is_includes)
          return false;
      }
      return true;
    }
  },
  mounted() {
  }
}
</script>

<style scoped lang="scss">
@import "../../scss/variables";

.borderLeft {
  border-left: 0.5em solid $color_primary;
}

.job {
  display: flex;
  flex-direction: column;
  background-color: white;
  border-radius: 5px;
  padding-left: 20px;
  margin: 0 30px 30px 30px;
  //border-left: 1px  solid;
  img {
    width: 4em;
  }
  .title {
    display: flex;
    align-items: center;
    margin-top: 15px;
    margin-bottom: 15px;
    h1 {
      font-size: 14px;
      color: $color_primary;
      font-weight: bold;

    }
    //justify-content: space-between;
    div {
      text-transform: uppercase;
      color: white;
      border-radius: 10px;
      padding: 7.5px;
      margin-left: 10px;
    }
    .new {
      background-color: $color_primary;
    }
    .featured {
      background-color: $color_tertiary;
    }
  }


  .line {
    height: 1px;
    background-color: gray;
    width: 100%;
    margin: 10px 10px 10px 0;
  }

  .infos {
    display: flex;
    .info {
      color: gray;
      display: flex;
      align-items: center;
      .point {
        width: 5px;
        height: 5px;
        border-radius: 50%;
        background-color: gray;
        margin-right: 7.5px;
        margin-left: 7.5px;

      }
    }
  }
  .filters {
    display: flex;
    flex-wrap: wrap;
    .filter {
      background-color: $color_secondary;
      color: $color_primary;
      font-weight: bold;
      padding: 10px;
      border-radius: 10px;
      margin-right: 20px;
      margin-bottom: 10px;
      cursor: pointer;
    }
  }
}
</style>