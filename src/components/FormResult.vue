<template>
  <div>
    <p>This is the result page</p>

    <ul>
      Profile Information
      <li v-for="(profile, index) in profileData" :key="`profile-${index}`">
        {{ profile }}
      </li>
    </ul>

    <ul>
      Address
      <li v-for="(address, index) in addressData" :key="`address-${index}`">
        {{ address }}
      </li>
    </ul>

    <ul>
      Login Information
      <li v-for="(login, index) in loginData" :key="`login-${index}`">
        {{ login }}
      </li>
    </ul>

    <ul>
      Optin Information
      <li v-for="(optin, index) in optinData" :key="`optin-${index}`">
        {{ optin }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    profileData: Object,
    addressData: Object,
    loginData: Object,
    optinData: Object,
  },
};
</script>

<style>
</style>