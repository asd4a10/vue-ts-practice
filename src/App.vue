<script setup lang="ts">
import { ref } from "vue";
import Job from "@/types/job.ts";
import JobListView from "./modules/job/views/JobListView.vue";
import OrderTerm from "@/types/OrderTerm.ts";

const jobs = ref<Job[]>([
  { title: "job title 1", location: "loc 1", salary: 10, id: 1 },
  { title: "job title 2", location: "2", salary: 15, id: 2 },
  { title: "job title 3", location: "3", salary: 20, id: 3 },
  { title: "job title 4", location: "4", salary: 25, id: 4 },
]);

const order = ref<OrderTerm>("title");
const handleSort = (term: OrderTerm) => {
  order.value = term;
};
</script>

<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleSort('title')">order by title</button>
        <button @click="handleSort('location')">order by location</button>
        <button @click="handleSort('salary')">order by salary</button>
      </div>
    </header>
    <JobListView :jobs="jobs" :order="order" />
  </div>
</template>

<style scoped>
header {
  max-width: 960px;
  margin: 40px auto;
  display: flex;
  justify-content: center;
}
header button {
  margin: 0 10px;
  padding: 10px;
  border: 1px grey solid;
  border-radius: 5px;
}
</style>
