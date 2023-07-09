<script setup lang="ts">
import { ref } from "vue";
import Job from "./types/job.ts";

const jobs = ref<Job[]>([
  { title: "job title 1", location: "loc 1", salary: 1 },
  { title: "job title 2", location: "2", salary: 1 },
  { title: "job title 3", location: "3", salary: 1 },
  { title: "job title 4", location: "4", salary: 1 },
]);
</script>

<template>
  <p>Jobs</p>
  <p>{{ jobs }}</p>
</template>

<style scoped></style>
