<template>
  <fieldset name="profile">
    <legend>Profile</legend>

    <!--prefix-->
    <label
      >Prefix
      <select name="prefix" v-model="profileObj.pre" @change="emitValues">
        <option selected disabled hidden>Pick One</option>
        <option
          v-for="(prefix, index) in prefixes"
          :key="`selection-${index}`"
          :value="prefix"
        >
          {{ prefix }}
        </option>
      </select>
    </label>

    <!--Name-->
    <label
      >First Name
      <input
        type="text"
        name="firstName"
        v-model="profileObj.fName"
        @change="emitValues" 
        required
      />
    </label>
    <label>
      Middle Name
      <input
        type="text"
        name="middleName"
        v-model="profileObj.mName"
        @change="emitValues"
      />
    </label>
    <label
      >Last Name
      <input
        type="text"
        name="lastName"
        v-model="profileObj.lName"
        @change="emitValues"
        required
      />
    </label>

    <!--suffix-->
    <label
      >Suffix
      <select name="suffix" v-model="profileObj.suff" @change="emitValues">
        <option selected disabled hidden>Pick One</option>
        <option
          v-for="(suffix, index) in suffixes"
          :key="`suffix-${index}`"
          :value="suffix"
        >
          {{ suffix }}
        </option>
      </select>
    </label>

    <!-- gender -->
    <fieldset name="gender">
      <legend>Gender</legend>
      <input type="radio" name="gender" value="female" id="female" v-model="profileObj.gender" @change="emitValues" required/>
      <label for="female">Female</label>
      <input type="radio" name="gender" value="male" id="male" v-model="profileObj.gender" @change="emitValues" required/>
      <label for="ale">Male</label>
      <input type="radio" name="gender" value="noAnswer" id="noAnswer" v-model="profileObj.gender" @change="emitValues" required/>
      <label for="noAnswer">Prefer not to answer</label>
    </fieldset>

    <!-- birthday -->
    <label>Birthday
      <input type="date" name="bday" v-model="profileObj.bday" @change="emitValues" required/>
      </label>

    <!-- end of fieldset -->
  </fieldset>
</template>

<script>
export default {
  props: {
    prefixes: Array,
    suffixes: Array,
  },
  data() {
    return {
      profileObj: {
        pre: "",
        fName: "",
        mName: "",
        lName: "",
        suff: "",
        bday: "",
        gender: "",
      },
    };
  },
  methods: {
    emitValues() {
      this.$emit("profile-input", this.profileObj);
    },
  },
};
</script>

<style>
</style>