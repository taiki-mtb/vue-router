<template>
  <div>
    <h3>Users</h3>
    <router-link to="/users/1">ユーザー１</router-link>
    <router-link to="/users/2">ユーザー２</router-link>
    <hr>
    <button @click="toHome">Homeに行く</button>
    <hr>
    <h1>User No. {{ id }}</h1>
    <router-link :to="'/users/' + (Number(id) + 1) + '/profile' ">次のユーザー</router-link>
    <router-view></router-view>
    <div style="height: 700px;"></div>
    <router-link
      id="next-user"
      :to="{ name: 'users-id-profile', params: { id: Number(id) + 1 }, query: { lang: 'ja', page: 2 }, hash: '#next-user' }"
      >次のユーザー</router-link>
    <div style="height: 1400px;"></div>
  </div>
</template>

<script>
  export default {
    props: ["id"],
    methods: {
      toHome() {
        this.$router.push("/");
      }
    },
    beforeRouteEnter(to, from, next) {
      next(vm => {
        console.log(vm.id);
      });
    },
    beforeRouteUpdate(to, from, next) {
      next();
    },
    beforeRouteLeave(to, from, next) {
      const isLeave = window.confirm("離れますか");
      if (isLeave) {
        next();
      } else {
        next(false);
      }
    }
  };
</script>