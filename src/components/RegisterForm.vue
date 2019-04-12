<!-- A signup form with pure css tooltips -->

<template>
  <main>
    <header>
      <h3>Signup Below</h3>
    </header>
    <section>
      <form @submit.prevent="onSubmit">
        <!-- tooltip text might be dynamically set through props -->
        <label
          for="username"
          data-tooltip="Username must be alphanumeric"
        >
          Username
        </label>
        <input
          id="username"
          v-model="form.username"
        >
        <label
          for="email"
          data-tooltip="Email must be a valid address"
        >
          Email
        </label>
        <input
          id="email"
          v-model="form.email"
        >
        <label
          for="password"
          data-tooltip="Password must be less than four characters"
        >
          Password
        </label>
        <input
          id="password"
          v-model="form.password"
        >
        <label
          for="confirmPassword"
          data-tooltip="Passwords have to match bro"
        >
          Confirm Password
        </label>
        <input
          id="confirmPassword"
          v-model="form.confirmPassword"
        >
        <button type="submit">Register</button>
      </form>
    </section>
  </main>
</template>

<script>
export default {
  name: "RegisterForm",
  data: function() {
    return {
      form: {
        username: "",
        email: "",
        password: "",
        confirmPassword: ""
      }
    };
  },
  methods: {
    onSubmit() {
      // do the validations....below is not the actual validations....
      if (this.form.password !== this.form.confirmPassword) {
        alert("invalid form");
        return;
      } else {
        // if valid do the things....
        let formData = {
          username: this.form.username,
          email: this.form.email,
          password: this.form.password
        };
      }
    }
  }
};
</script>

<style lang="scss" scoped>
main {
  width: 80%;
  max-width: 500px;
  border: 2px solid #909ebd;
  border-radius: 5px;
  color: #7a7a7a;
  padding: 1rem;
}
header {
  h3 {
    border-bottom: 1px solid #909ebd;
    text-align: left;
  }
}
section {
  form {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-start;

    label {
      line-height: 2rem;
      position: relative;
      &::before {
        content: "";
        position: absolute;
        border-width: 10px 8px 0 8px;
        border-style: solid;
        border-color: rgba(#657eb3, 0.8) transparent transparent transparent;
        right: -12px;
        top: -3px;
      }
      &::after {
        position: absolute;
        color: #ffffff;
        content: attr(data-tooltip);
        background-color: rgba(101, 126, 179, 0.8);
        border-radius: 5px;
        padding: 5px;
        width: 250px;
        font-size: 12px;
        top: -45px;
        right: -249px;
      }
      &::before,
      &::after {
        opacity: 0;
        transition: all ease 200ms;
      }
      &:hover::before,
      &:hover::after {
        opacity: 1;
      }
    }

    input {
      width: 75%;
      border: 1px solid #909ebd;
      border-radius: 5px;
      font-size: 1.5rem;
      margin-bottom: 10px;
    }

    button {
      font-size: 1.5rem;
      margin-top: 15px;
      padding: 0.75rem 2rem;
      color: #ffffff;
      background-color: rgba(#587ac2e3, 0.5);
      border: none;
      border-radius: 5px;
      transition: all 200ms;
      outline: none;
      cursor: pointer;
      &:hover {
        transform: translate(-1px, -2px);
        box-shadow: 3px 3px rgba(#cccccc, 0.5);
      }
      &:active {
        transform: translate(0, 0);
        box-shadow: none;
      }
    }
  }
}
</style>