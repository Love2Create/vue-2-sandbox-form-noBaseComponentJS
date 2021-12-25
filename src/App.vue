<template>
  <div id="app">
    <!-- form starts here -->
    <form>
      <!-- form result -->
      <FormResult
        v-if="formComplete"
        :profileData="profileData"
        :addressData="addressData"
        :loginData="loginData"
        :optinData="optinData"
      />

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

      <!-- login -->
      <FieldsetLogin
        v-if="!formComplete"
        :loginData="loginData"
        @login-entry="loginEntry"
      />

      <!-- optin -->
      <FieldsetOptin
        v-if="!formComplete"
        @optin-entry="optinEntry"
        :optinData="optinData"
      />

      <!-- button -->
      <FormButton
        v-if="!formComplete"
        buttonText="Finished"
        @btn-clicked="btnClicked"
      />
    </form>
    <!-- form ends here -->
  </div>
</template>

<script>
import FieldsetProfile from "./components/FieldsetProfile.vue";
import FieldsetAddress from "./components/FieldsetAddress.vue";
import FormButton from "./components/FormButton.vue";
import FormResult from "./components/FormResult.vue";
import FieldsetLogin from "./components/FieldsetLogin.vue";
import FieldsetOptin from "./components/FieldsetOptin.vue";

export default {
  components: {
    FieldsetProfile,
    FieldsetAddress,
    FormButton,
    FormResult,
    FieldsetLogin,
    FieldsetOptin,
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
      stateArray: [
        "Alabama",
        "Alaska",
        "American Samoa",
        "Arizona",
        "Arkansas",
        "California",
        "Colorado",
        "Connecticut",
        "Delaware",
        "District of Columbia",
        "Federated States of Micronesia",
        "Florida",
        "Georgia",
        "Guam",
        "Hawaii",
        "Idaho",
        "Illinois",
        "Indiana",
        "Iowa",
        "Kansas",
        "Kentucky",
        "Louisiana",
        "Maine",
        "Marshall Islands",
        "Maryland",
        "Massachusetts",
        "Michigan",
        "Minnesota",
        "Mississippi",
        "Missouri",
        "Montana",
        "Nebraska",
        "Nevada",
        "New Hampshire",
        "New Jersey",
        "New Mexico",
        "New York",
        "North Carolina",
        "North Dakota",
        "Northern Mariana Islands",
        "Ohio",
        "Oklahoma",
        "Oregon",
        "Palau",
        "Pennsylvania",
        "Puerto Rico",
        "Rhode Island",
        "South Carolina",
        "South Dakota",
        "Tennessee",
        "Texas",
        "Utah",
        "Vermont",
        "Virgin Island",
        "Virginia",
        "Washington",
        "West Virginia",
        "Wisconsin",
        "Wyoming",
      ],

      profileData: {},
      addressData: {},
      loginData: {},
      optinData: {},
    };
  },
  methods: {
    btnClicked() {
      this.formComplete = true;
      console.log(this.optinData);
    },

    profileInput(profileObj) {
      this.profileData = profileObj;
    },

    addressInput(addressObj) {
      this.addressData = addressObj;
    },

    loginEntry(loginObj) {
      this.loginData = loginObj;
    },
    optinEntry(optinObj) {
      this.optinData = optinObj;
      // console.log(this.optinData);
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
