/** * Created by vouill on 11/13/17. */

<template>
  <div>
    <!--
      It seems that the submit event is skipped and replaced by
      method `login()`. Therefore, when clicking the "Login" button,
      the method `login()` will be called to perform login action.
     -->
    <form class="login" @submit.prevent="login">
      <h1>Sign in</h1>
      <label>User name</label>
      <!-- Input `username` is binded to Vue data model `username` -->
      <input required v-model="username" type="text" placeholder="Snoopy" />
      <label>Password</label>
      <!-- Input `password` is binded to Vue data model `password` -->
      <input
        required
        v-model="password"
        type="password"
        placeholder="Password"
      />
      <hr />
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<style>
.login {
  display: flex;
  flex-direction: column;
  width: 300px;
  padding: 10px;
}
</style>

<script>
// TODO document the behavior of actions/auth
import { AUTH_REQUEST } from "actions/auth";

export default {
  name: "login",
  data() {
    return {
      username: "dogo",
      password: "dogy"
    };
  },
  methods: {
    login: function() {
      // capture data available in this class and save they as
      // variables `username` and `password`.
      const { username, password } = this;
      // TODO
      this.$store.dispatch(AUTH_REQUEST, { username, password }).then(() => {
        this.$router.push("/");
      });
    }
  }
};
</script>
