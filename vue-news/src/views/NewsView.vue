<template>
  <div>
    <div v-for="user in users" v-bind:key="user.id">{{ user }}</div>
  </div>
</template>

<script>
import { fetchNewsList } from "../api/index.js";

export default {
  data() {
    return {
      users: [],
    };
  },
  created() {
    fetchNewsList()
      .then((response) => {
        this.users = response.data;
      })
      .catch(
        // 에러처리 이따구로 하지 말자
        (error) => console.log(error)
      );
  },
};
</script>

<style></style>
