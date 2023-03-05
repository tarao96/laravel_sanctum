<template>
  <div>
    ダッシュボード画面
    <button @click="getUsers">get users</button>
    <button @click="logout">Logout</button>
  </div>
</template>

<script>
export default ({
  methods: {
    async getUsers() {
      this.$axios.defaults.withCredentials = true;
      await this.$axios.get("http://localhost/api/users").then((res) => {
        console.log(res.data);
      });
    },
    async logout() {
      this.$axios.defaults.withCredentials = true;
      await this.$axios.post("http://localhost/api/logout").then((res) => {
        console.log(res.data);
      });
    },
  },
});
</script>
