<template>
  <div class="container">
    <header-component class="header"></header-component>
    <register-form-component
      class="register"
      @regData="(payload) => doSmth(payload)"
    ></register-form-component>
  </div>
</template>

<script setup>
import RegisterFormComponent from '../components/RegisterFormComponent.vue';
import HeaderComponent from '../components/HeaderComponent.vue';
// const emits = defineEmits(['regData']);
const doSmth = (proxy) => {
  console.log(proxy.value);
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
  background-color: black
  .register
    position: sticky
    top: 5%
    right: 10%
</style>
