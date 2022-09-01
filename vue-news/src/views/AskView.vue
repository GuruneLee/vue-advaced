<template>
  <div>ask</div>
</template>

<script>
import { fetchAskList } from "../api/index.js";

export default {
  name: "AskView",
  data() {
    return {
      ask: [],
    };
  },
  created() {
    fetchAskList()
      .then((response) => {
        this.ask = response.data;
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style></style>
