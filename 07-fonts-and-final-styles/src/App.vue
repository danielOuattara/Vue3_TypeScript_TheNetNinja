<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleOrderBy('title')">order by title</button>
        <button @click="handleOrderBy('location')">order by location</button>
        <button @click="handleOrderBy('salary')">order by salary</button>
      </div>
    </header>

    <JobsList :jobs="jobs" :orderTerm="orderTerm" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Job from "./types/Job";
import jobsList from "./data/jobs-data";
import JobsList from "./components/JobsList.vue";
import OrderBy from "./types/OrderBy";

export default defineComponent({
  name: "App",
  components: { JobsList },
  setup() {
    const jobs = ref<Job[]>(jobsList);

    const orderTerm = ref<OrderBy>("title");

    function handleOrderBy(orderArg: OrderBy) {
      // console.log(arg);
      // if (arg == "title" || arg == "location") {
      //   return 0;
      // } else if (arg == "salary") {
      //   return (jobs.value = jobs.value.sort(function (a, b: Job) {
      //     return a.salary - b.salary;
      //   }));
      // }
      // return 0;

      orderTerm.value = orderArg;
    }

    return {
      jobs,
      orderTerm,
      handleOrderBy,
    };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
