<script setup lang="ts">
import { computed, PropType } from "vue";
import Job from "@/types/job.ts";
import OrderTerm from "@/types/OrderTerm.ts";

const props = defineProps({
  jobs: {
    type: Array as PropType<Job[]>,
    default: [],
  },
  order: {
    type: String as PropType<OrderTerm>,
    required: true,
  },
});

const orderedJobs = computed(() => {
  return [
    ...props.jobs?.sort((a: Job, b: Job) => {
      return a[props.order] <= b[props.order] ? -1 : 1;
    }),
  ];
});
</script>

<template>
  <div class="job-list">
    <p align="right">Ordered by {{ order }}</p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }} tenge</p>
        </div>
        <div class="description">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusamus
          accusantium animi at consectetur culpa earum expedita hic impedit
          ipsum, maxime mollitia neque obcaecati odio odit officia officiis
          rerum vitae voluptatibus?
        </div>
      </li>
    </ul>
  </div>
</template>

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
