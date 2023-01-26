<template>
  <div class="app">
    <p>{{ name1 }} - {{ age1 }}</p>
    <p>
      <button @click="changeName1('Daniel')">change name</button>
    </p>
    <p>
      <button @click="changeAge1('40')">change age</button>
    </p>

    <hr />

    <p>{{ name2 }} - {{ age2 }}</p>
    <p>
      <button @click="changeName2('Julie')">change name</button>
    </p>
    <p>
      <button @click="changeAge2('38')">change age</button>
    </p>

    <div v-for="job in jobs" :key="job.id">
      <h2>{{ job.title }}</h2>
      <p>{{ job.location }}</p>
      <p>{{ job.salary }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import Job from "./types/Job";
import jobsData from "./data/jobs-data";

export default defineComponent({
  name: "App",
  setup() {
    /* using reactive function
    ---------------------------*/
    const state = reactive({
      name1: "Link",
      age1: 39 as number | string, // type assertion
    });

    console.log(state);

    /* using ref function
    ---------------------------*/
    const name2 = ref("Link");
    const age2 = ref<number | string>(39);

    function changeName1(name: string) {
      return (state.name1 = name);
    }

    function changeAge1(age: number | string) {
      return (state.age1 = age);
    }

    function changeName2(name: string) {
      return (name2.value = name);
    }

    function changeAge2(age: number | string) {
      return (age2.value = age);
    }

    // const jobs = ref<Job[]>([
    //   {
    //     title: "farm worker",
    //     location: "lon lon ranch",
    //     salary: 30000,
    //     id: "1",
    //   },
    //   {
    //     title: "quarryman",
    //     location: "death mountain",
    //     salary: 40000,
    //     id: "2",
    //   },
    //   {
    //     title: "flute player",
    //     location: "the lost woods",
    //     salary: 35000,
    //     id: "3",
    //   },
    //   { title: "fisherman", location: "lake hylia", salary: 21000, id: "4" },
    //   {
    //     title: "prison guard",
    //     location: "gerudo valley",
    //     salary: 32000,
    //     id: "5",
    //   },
    // ]);
    const jobs = ref<Job[]>(jobsData);

    return {
      ...toRefs(state),
      name2,
      age2,
      changeName1,
      changeAge1,
      changeName2,
      changeAge2,
      jobs,
    };
  },
});
</script>

<style></style>
