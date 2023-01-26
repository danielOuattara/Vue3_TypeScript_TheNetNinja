<template>
  <div class="job-list">
    <p>ordered by {{ orderTerm }}</p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Totam eum
            vitae nostrum nisi nobis dignissimos accusantium ut doloremque nihil
            aspernatur? Id minima necessitatibus maxime. Esse odit totam beatae
            eligendi iure.
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
// import jobsList from "@/data/jobs-data";
import Job from "@/types/Job";
import OrderBy from "@/types/OrderBy";
import { defineComponent, PropType, computed } from "vue";

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>,
    },
    orderTerm: {
      required: true,
      type: String as PropType<OrderBy>,
    },
  },
  setup(props) {
    const orderedJobs = computed(function () {
      return [...props.jobs].sort(function (a: Job, b: Job) {
        return a[props.orderTerm] > b[props.orderTerm] ? 1 : -1;
      });
    });

    return {
      orderedJobs,
    };
  },
});
</script>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}
</style>
