<template>
  <fieldset>
    <label
      >Email Address
      <input
        v-model="loginObj.emailaddress"
        type="email"
        name="emailAddress"
        placeholder="johndoe@gmail.com"
        @change="emitValue"
        required
      />
    </label>
    <label
      >Password
      <input
        v-model="loginObj.password1"
        type="password"
        name="password1"
        @change="emitValue"
        required
      />
    </label>
    <label
      >Confirm Password
      <input
        v-model="loginObj.password2"
        type="password"
        name="password2"
        @change="emitValue"
        required
      />
    </label>
  </fieldset>
</template>

<script>
export default {
  data() {
    return {
      loginObj: {
        emailAddress: "",
        password1: "",
        password2: "",
      },
    };
  },
  methods: {
    emitValue() {
      this.$emit("login-entry", this.loginObj);
    },
  },
};
</script>

<style>
</style>