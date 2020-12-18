<template>
  <div id="app">
    <div id="nav">
      <div class="alert alert-success" v-if="flashMessage" v-on:click="flashMessage = ''">
        {{ flashMessage }}
      </div>
      <router-link to="/">Home</router-link>
      |
      <router-link to="/create">Create</router-link>
      |
      <router-link v-if="!isLoggedin()" to="/signup">Signup</router-link>
      |
      <router-link v-if="!isLoggedin()" to="/login">Login</router-link>
      |
      <router-link v-if="isLoggedin()" to="/logout">Logout</router-link>
    </div>

    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
<script>
export default {
  data: function() {
    return {
      flashMessage: "WHY NO WORK?",
    };
  },
  methods: {
    isLoggedin: function() {
      if (localStorage.getItem("jwt")) {
        return true;
      } else {
        return false;
      }
    },
    getUserId: function() {
      return localStorage.getItem("user_id");
    },
  },
};
</script>
