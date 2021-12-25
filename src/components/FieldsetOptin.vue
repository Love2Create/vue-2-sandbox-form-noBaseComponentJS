<template>
  <fieldset>
    <legend>Optins</legend>
    <label
      >
      <input v-model="optinObj.subscribe" type="checkbox" name="newsletter1" @change="emitValue" />
    Subscribe to our weekly newsletter</label>
    <label
      >
      <input v-model="optinObj.taf" type="checkbox" name="TAF" @change="toggle"/>Tell a friend
      <fieldset v-if="tafToggle">
        <label
          >
          <input v-model="optinObj.friendEmail" type="email" @change="emitValue"/>
        My friend's email address</label>
      </fieldset>
    </label>
  </fieldset>
</template>

<script>
export default {
  data(){
      return{
          optinObj:{
              subscribe:"",
              taf:"",
              friendEmail:"",
          },
          tafToggle:false,
      }
  },
  methods:{
      emitValue(){
          this.$emit("optin-entry", this.optinObj);
      },
      toggle(){
          this.tafToggle=!this.tafToggle;
      }
  }
};
</script>

<style>
</style>