<script setup lang="ts">
import { ref } from "vue";
import Job from "@/types/job.ts";
import JobListView from "./modules/job/views/JobListView.vue";

const jobs = ref<Job[]>([
  { title: "job title 1", location: "loc 1", salary: 10, id: 1 },
  { title: "job title 2", location: "2", salary: 15, id: 2 },
  { title: "job title 3", location: "3", salary: 20, id: 3 },
  { title: "job title 4", location: "4", salary: 25, id: 4 },
]);
</script>

<template>
  <JobListView :jobs="jobs" />
</template>

<style scoped></style>
