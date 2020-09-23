<template>
  <div class="signup">
    <div class="container">
      <h4>Sign Up</h4>
    </div>
    <form @submit.prevent="signup">
      <div class="form-group">
        <label for="name">Name</label>
        <input
          type="text"
          placeholder="Enter name"
          id="name"
          name="name"
          v-model="form.name"
          class="input"
        />
      </div>

      <div class="form-group">
        <label for="email">Email</label>
        <input
          type="email"
          placeholder="Enter email"
          id="email"
          name="email"
          v-model="form.email"
          class="input"
        />
      </div>

      <div class="form-group">
        <label for="password">Password</label>
        <input
          type="password"
          placeholder="Enter Password"
          id="password"
          name="password"
          v-model="form.password"
          class="input"
        />
      </div>

      <div class="form-group">
        <label for="confirm">Confirm Password</label>
        <input
          type="password"
          placeholder="Confirm Password"
          id="confirm"
          name="confirm"
          v-model="form.confirm"
          class="input"
        />
      </div>
      <div class="form-group">
        <button type="submit" class="btn">Sign Up</button>
      </div>
    </form>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "SignUp",
  data() {
    return {
      form: {
        name: "",
        email: "",
        password: "",
        confirm: ""
      }
    };
  },
  methods: {
    ...mapActions({ signIn: "auth/signup" }),
    signup() {
      this.signUp(this.form)
        .then(() => {
          // redirect to dashboard
          this.$router.push("dashboard");
        })
        .catch(() => {
          console.log("failed");
        });
    }
  }
};
</script>

<style lang="scss" scoped>
h4 {
  text-align: center;
  font-size: 1.6rem;
  margin: 1rem 0;
  font-family: "Fira Code";
  color: skyblue;
}
form {
  width: 500px;
  box-shadow: 0 0 0.5rem #ccc;
  margin: auto;
  padding: 1rem;
  box-sizing: border-box;

  label {
    font-size: 0.9rem;
    color: skyblue;
  }

  .form-group {
    display: flex;
    flex-direction: column;

    .input {
      margin-bottom: 1rem;
      margin-top: 0.2rem;
    }
  }

  .btn {
    cursor: pointer;
    background: skyblue;
    width: 120px;
    padding: 0.5rem 1.4rem;
    border: 1px solid transparent;
    border-radius: 0.2rem;
    color: #fff;
    transition: all 0.3s;

    &:hover {
      border-color: skyblue;
      background: transparent;
      color: #212226;
    }
  }
}
</style>
