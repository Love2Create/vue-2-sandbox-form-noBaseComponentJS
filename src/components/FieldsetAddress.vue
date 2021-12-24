<template>


  <fieldset name="address">
      <legend>Address</legend>

    <!-- physical address -->
    <template v-if="physicalAddress">
      <label
        >Address (Line 1)
        <input type="text" name="addressLine1" v-model="addressObj.addressLine1" @change="emitValues"/>
      </label>

      <label
        >Address (Line 2)
        <input type="text" name="addressLine2" v-model="addressObj.addressLine2" @change="emitValues"/>
      </label>

      <label
        >City
        <input type="text" value="city" v-model="addressObj.city"/>
      </label>

      <label
        >State
        <select name="state" v-model="addressObj.state" @change="emitValues">
          <option selected disabled hidden>Pick One</option>
          <option
            v-for="(state, index) in states"
            :key="`state-${index}`"
            :value="state"
          >
            {{ state }}
          </option>
        </select>
      </label>

      <label
        >Zip Code
        <input input="number" value="zipCode" v-model="addressObj.zipCode"/>
      </label>
    </template>

    <!-- email address -->
    <label>Email Address
      <input type="email" name="email" v-model="addressObj.email" @change="emitValues"/>
    </label>

  </fieldset>
</template>

<script>
export default {
  props: {
    physicalAddress: Boolean,
    states: Array,
  },
  data() {
    return {
      addressObj: {
        addressLine1: "",
        addressLine2: "",
        city: "",
        state: "",
        zip: "",
        email:"",
      },
    };
  },
  methods:{
      emitValues(){
          this.$emit("address-input",this.addressObj);
      }
  }
};
</script>

<style>
</style>