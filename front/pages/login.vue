<template>
  <div class="form-wrapper">
    <div class="card">
      <div class="form-group">
        <div class="form">
          <label for="name">Name</label>
          <input type="text" id="name" v-model="form.name" />
        </div>
        <div class="form">
          <label for="email">E-mail</label>
          <input type="email" id="email" v-model="form.email" />
        </div>
        <div class="form">
          <label for="password">Password</label>
          <input type="password" id="password" v-model="form.password" />
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
      form: {
        name: "",
        email: "",
        password: "",
      },
    };
  },
  methods: {
    login() {
      this.$axios.get("/sanctum/csrf-cookie").then((response) => {
        this.$axios
          .post("http://localhost/login", { form })
          .then((response) => {
            console.log(response.data);
          });
      });
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
  height: 10%;
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
