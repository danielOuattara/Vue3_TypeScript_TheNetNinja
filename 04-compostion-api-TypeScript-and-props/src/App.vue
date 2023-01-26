<template>
  <div class="app">
    <JobsList :jobs="jobs" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Job from "./types/Job";
import jobsList from "./data/jobs-data";
import JobsList from "./components/JobsList.vue";

export default defineComponent({
  name: "App",
  components: { JobsList },
  setup() {
    const jobs = ref<Job[]>(jobsList);

    return {
      jobs,
    };
  },
});
</script>

<style></style>
