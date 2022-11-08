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
const doSmth = (proxy) => {
  console.log(proxy.value);
};
</script>

<style lang="sass" scoped>
.container
  position: relative
  min-height: 100vh
  width: 100%
  display: flex
  align-items: center
  justify-content: center
  background-color: black
  .header
    z-index: 6
  .register
    position: absolute
    top: 15%
    right: 10%
    z-index: 5
</style>
