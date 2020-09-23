<template>
  <div class="nav">
    <div class="container">
      <h1>CyberCode</h1>
      <ul class="nav-item">
        <router-link to="/">Home</router-link>

        <template v-if="authenticated">
          <router-link to="/dashboard">Dashboard</router-link>
          <p class="name">{{ user.name }}</p>
          <a href @click.prevent="signout">Logout</a>
        </template>
        <template v-else>
          <router-link to="/signin">Sign In</router-link>
          <router-link to="/signup">Sign Up</router-link>
        </template>
      </ul>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  name: "Navigation",
  computed: {
    ...mapGetters({
      authenticated: "auth/authenticated",
      user: "auth/user"
    })
  },
  methods: {
    ...mapActions({ signOut: "auth/signOut" }),
    signout() {
      this.signOut().then(() => {
        this.$router.replace({ name: "home" });
      });
    }
  }
};
</script>

<style lang="scss">
.nav {
  width: 100%;
  background: #212226;

  .container {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  h1 {
    margin: 0;
    font-family: cursive;
    color: #fff;
  }
  .nav-item {
    a,
    .name {
      display: inline-block;
      margin-left: 1rem;
      text-decoration: none;
      color: #ccc;

      &.active,
      &:hover {
        color: skyblue;
      }
    }
  }
}

.container {
  max-width: 1200px;
  margin: auto;
}
</style>
