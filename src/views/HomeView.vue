<template>
  <div class="container">
    <register-form-component
      @regData="(payload) => doSmth(payload)"
    ></register-form-component>
  </div>
</template>

<script setup>
import RegisterFormComponent from '../components/RegisterFormComponent.vue';
// const emits = defineEmits(['regData']);
const doSmth = (el) => {
  console.log(el);
};
</script>

<style lang="sass" scoped>
.container
  min-height: 100vh
  width: 100%
  display: flex
  // place-items: center
  align-items: center
  justify-content: center
</style>
