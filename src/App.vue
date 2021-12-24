<template>
  <div id="app">

    <!-- start -->

    <!-- form result -->
    <FormResult v-if="formComplete" :formStatus="formComplete" :profileDataArray="profileDataArray"/>

  <!-- profile -->
    <FieldsetProfile
      v-if="!formComplete"
      :prefixes="prefixArray"
      :suffixes="suffixArray"
      @profile-input="profileInput"
    />

    <!-- address -->
    <FieldsetAddress
      v-if="!formComplete"
      :physicalAddress="physicalAddressShow"
      @address-input="addressInput"
      :states="stateArray"
    />

    <!-- button -->
    <FormButton
      v-if="!formComplete"
      buttonText="Finished"
      @btn-clicked="btnClicked"
    />
  </div>
</template>

<script>
import FieldsetProfile from "./components/FieldsetProfile.vue";
import FieldsetAddress from "./components/FieldsetAddress.vue";
import FormButton from "./components/FormButton.vue";
import FormResult from "./components/FormResult.vue";

export default {
  components: {
    FieldsetProfile,
    FieldsetAddress,
    FormButton,
    FormResult,
  },
  data() {
    return {

      // button
      btnText: "click me",
      formComplete: false,

      // fieldset Profile
      prefixArray: ["Mr.", "Ms.", "Mrs.", "None"],
      suffixArray: ["Sr.", "Jr.", "I", "II", "III", "None"],

      // fieldset address
      physicalAddressShow: true,
      stateArray: ['Alabama','Alaska','American Samoa','Arizona','Arkansas','California','Colorado','Connecticut','Delaware','District of Columbia','Federated States of Micronesia','Florida','Georgia','Guam','Hawaii','Idaho','Illinois','Indiana','Iowa','Kansas','Kentucky','Louisiana','Maine','Marshall Islands','Maryland','Massachusetts','Michigan','Minnesota','Mississippi','Missouri','Montana','Nebraska','Nevada','New Hampshire','New Jersey','New Mexico','New York','North Carolina','North Dakota','Northern Mariana Islands','Ohio','Oklahoma','Oregon','Palau','Pennsylvania','Puerto Rico','Rhode Island','South Carolina','South Dakota','Tennessee','Texas','Utah','Vermont','Virgin Island','Virginia','Washington','West Virginia','Wisconsin','Wyoming'],
    };
  },
  methods: {
    btnClicked() {
      this.formComplete = true;
    },

    profileInput(profileObj) {
      console.log(profileObj);
    },

    addressInput(addressObj) {
      console.log(addressObj);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
fieldset {
  width: 50%;
}
</style>
