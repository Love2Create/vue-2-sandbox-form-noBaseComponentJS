<template>
  <button @click="emitValue">{{ buttonText }}</button>
</template>

<script>
export default {
props:{
    buttonText: String,
    formStatus: Boolean,
},
methods:{
    emitValue(){
        this.$emit("btn-clicked");
    }
}
}
</script>

<style>

</style>