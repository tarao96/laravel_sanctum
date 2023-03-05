<template>
  <div class="form-wrapper">
    <div class="card">
      <div class="form-group">
        <div class="form">
          <label for="name">Name</label>
          <input type="text" id="name" v-model="name" />
        </div>
        <div class="form">
          <label for="email">E-mail</label>
          <input type="email" id="email" v-model="email" />
        </div>
        <div class="form">
          <label for="password">Password</label>
          <input type="password" id="password" v-model="password" />
        </div>
        <button @click="login">Login</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async login() {
      try {
        await this.$auth
          .loginWith("laravelSanctum", {
            data: {
              email: this.email,
              password: this.password,
            },
          })
          .then((res) => {
            console.log(res.data);
            this.$router.push("/dashboard");
          })
          .catch((err) => {
            console.log(err.response);
          });
      } catch (error) {
        window.alert("ログイン認証失敗");
        console.log(error);
      }
    },
  },
};
</script>

<style scoped>
.form-wrapper {
  height: 100vw;
  display: flex;
  justify-content: center;
  padding-top: 50px;
}
.form-wrapper > .card {
  background: #223a70;
  width: 50%;
  height: 15%;
  display: flex;
  align-items: center;
}
.form-wrapper > .card > .form-group {
  margin-left: 30px;
}
.form-wrapper > .card > .form-group > .form {
  margin-bottom: 20px;
}
.form-wrapper > .card > .form-group > .form > label {
  color: #fff;
}
</style>
