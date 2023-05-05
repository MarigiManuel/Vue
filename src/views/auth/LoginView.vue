<template>
  <div class="container mt-5">
    <div class="row d-flex justify-content-center">
      <div class="col-md-6 shadow-lg p-5">
        <h3>Login</h3>
        <form class="mt-2" @submit.prevent="login()">
          <div class="mb-3">
            <label for="name" class="form-label">Email</label>
            <input
              type="email"
              class="form-control"
              id="email"
              name="email"
              placeholder="Email"
              v-model="user.email"
            />
          </div>
          <div class="mb-3">
            <label for="duration" class="form-label">Password</label>
            <input
              type="password"
              class="form-control"
              id="password"
              name="password"
              placeholder="Password"
              v-model="user.password"
            />
          </div>
          <div class="mb-3">
            <button class="btn btn-primary">Login</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<script>
import { useAuthStore } from "../../stores/auth";
export default {
  setup() {
    let authStore = useAuthStore();
    return {
      authStore,
    };
  },
  data() {
    return {
      user: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    login() {
      this.authStore.user = this.user;
      this.authStore.login();
      this.user.email = "";
      this.user.password = "";
      this.$router.replace("/crops");
      console.log(this.user);
    },
  },
};
</script>
<style></style>
