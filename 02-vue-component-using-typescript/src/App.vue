<template>
  <div class="app">
    <p>{{ name }} - {{ age }}</p>
    <p>
      <button @click="name = 'Julie'">change name</button>
    </p>
    <p>
      <button @click="changeName('Daniel')">change name</button>
    </p>
    <p>
      <button @click="changeAge('40')">change age</button>
    </p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
  components: {},
  data() {
    return {
      name: "Link",
      age: 39 as number | string, // type assertion
    };
  },
  methods: {
    changeName(name: string) {
      return (this.name = name);
    },
    changeAge(age: number | string) {
      return (this.age = age);
    },
  },
});
</script>

<style></style>
