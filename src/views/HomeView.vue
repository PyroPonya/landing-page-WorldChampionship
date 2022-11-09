<template>
  <div class="container">
    <header-component
      class="header"
      @setLang="(payload) => updateLanguage(payload)"
      @requestLogin="toggleLoginForm"
      @requestRegister="registerFormDisplay = !registerFormDisplay"
    ></header-component>
    <slider-component class="slider"></slider-component>
    <register-form-component
      class="register"
      :style="registerFormDisplay ? 'display: block' : 'display:none'"
      @regData="(payload) => apiRegisterData(payload)"
    ></register-form-component>
    <div class="info__btn"></div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import RegisterFormComponent from '../components/RegisterFormComponent.vue';
import HeaderComponent from '../components/HeaderComponent.vue';
import SliderComponent from '../components/SliderComponent.vue';
const registerFormDisplay = ref(true);
const apiRegisterData = (proxyData) => {
  console.log(proxyData);
};
const updateLanguage = (lang) => {
  console.log(lang);
};
const toggleLoginForm = () => {
  console.log('LET ME IN!');
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
  .slider
    height: 100vh
  .register
    position: absolute
    top: 15%
    right: 10%
    z-index: 5
  .info__btn
    position: absolute
    bottom: 2%
    right: calc(10% - 80px)
    height: 45px
    width: 40px
    background: url('/src/assets/info_btn.svg')
    background-repeat: no-repeat
    background-position: center
    cursor: pointer
    &:hover
      background: url('/src/assets/info_btn_hover.svg')
    &:active
      background: url('/src/assets/info_btn_active.svg')
</style>
