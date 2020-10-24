<template>
  <div>
    <h3>Users</h3>
    <router-link to="/users/1">ユーザー１</router-link>
    <router-link to="/users/2">ユーザー２</router-link>
    <hr>
    <button @click="toHome">Homeに行く</button>
    <hr>
    <h1>User No. {{ id }}</h1>
  </div>
</template>

<script>
  export default {
    props: ["id"],
    methods: {
      toHome() {
        this.$router.push("/");
      }
    }
  };
</script>