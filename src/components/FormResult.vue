<template>
<div>
  <p>This is the result page</p>

  <ul>Profile Information
    <li v-for="(profile, index) in profileDataArray" :key="`profile-${index}`">{{ profile }}</li>
    </ul>

    </div>
</template>

<script>
export default {
  props:{
    profileDataArray: Array,
  }

}
</script>

<style>

</style>