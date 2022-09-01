<template>
  <div>jobs</div>
</template>

<script>
import { fetchJobsList } from "../api/index.js";

export default {
  name: "JobsView",
  data() {
    return {
      jobs: [],
    };
  },
  created() {
    fetchJobsList()
      .then((response) => {
        this.jobs = response.data;
      })
      .catch(
        (error) => console.log(error)
      );
  },
};
</script>

<style></style>