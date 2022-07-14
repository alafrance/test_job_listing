<template>
  <div class="jobs">
    <div v-for="job in jobs" :key="job.id">
      <Job
          :image="job.logo"
          :title="job.company"
          :is-new="job.new"
          :is-featured="job.featured"
          :job-name="job.position"
          :infos="[job.postedAt, job.contract, job.location]"
          :roles="[job.role]"
          :levels="[job.level]"
          :languages="job.languages"
          :tools="job.tools"
      />
    </div>
  </div>
</template>

<script>
import Job from "./Job";
import jobs from "../../data.json";

export default {
  name: "ListJob",
  data() {
    return {
      jobs: jobs
    }
  },
  components: {Job},
}
</script>

<style scoped lang="scss">
@import "../../scss/variables";
  .jobs {
    padding-top: 50px;
  }
</style>