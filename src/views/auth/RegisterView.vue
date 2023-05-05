<template>
  <div class="container mt-5">
    <div class="row d-flex justify-content-center">
      <div class="col-md-6 shadow-lg p-5">
        <h3>Register</h3>
        <form class="mt-2" @submit.prevent="register()">
          <div class="mb-3">
            <label for="name" class="form-label">Name</label>
            <input
              type="text"
              class="form-control"
              id="name"
              name="name"
              placeholder="name"
              v-model="user.name"
            />
          </div>
          <div class="mb-3">
            <label for="email" class="form-label">Email</label>
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
            <div class="mb-3">
              <label for="duration" class="form-label">Confirm Password</label>
              <input
                type="password"
                class="form-control"
                id="password_confirmation"
                name="password_confirmation"
                placeholder="password_confirmation"
                v-model="user.password_confirmation"
              />
            </div>
            <button class="btn btn-primary">Register</button>
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
        name: "",
        email: "",
        password: "",
        password_confirmation: "",
      },
    };
  },
  methods: {
    register() {
      this.authStore.user = this.user;
      this.authStore.register();
      this.user.name = "";
      this.user.email = "";
      this.user.password = "";
      this.user.password_confirmation = "";
      this.$router.replace("/login");
      console.log(this.user);
    },
  },
};
</script>
<style></style>
