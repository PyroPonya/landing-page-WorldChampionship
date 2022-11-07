<template>
  <div class="container">
    <register-form-component></register-form-component>
  </div>
</template>

<script setup>
import RegisterFormComponent from '../components/RegisterFormComponent.vue';
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
