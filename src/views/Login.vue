<template>
  <div>
    <div class="row">
      <div class="card mx-auto">
        <div class="card-header text-white">
          <h4>Login</h4>
        </div>
        <div class="card-body">
          <form @submit.prevent="loginUser">
            <div class="form-group">
              <label for="username">Username</label>
              <input
                id="username"
                type="text"
                placeholder="Username"
                name="username"
                v-model="username"
                class="form-control"
              />
            </div>
            <div class="form-group">
              <label for="password">Password</label>
              <input
                type="password"
                class="form-control"
                placeholder="Password"
                name="password"
                id="password"
                v-model="password"
              />
            </div>
            <br />
            <input type="submit" class="btn text-white" value="Login" />
            <br />
            <br />
            <router-link to="/register" class="card-link"
              >Need and account?</router-link
            >
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    ...mapActions(["login"]),
    loginUser() {
      let user = {
        username: this.username,
        password: this.password,
      };
      this.login(user)
        .then((res) => {
          if (res.data.success) {
            this.$router.push("/profile");
          }
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style scoped>
.card {
  width: 40%;
  border-radius: 60;
}
.btn {
  border-radius: 0;
  background-color: black;
}
.form-control {
  border-radius: 0;
}
.card-header {
  background-color: black;
}
</style>