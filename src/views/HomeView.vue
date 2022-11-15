<template>
  <div class="container">
    <header-component
      class="header"
      :store="store"
      :currentLanguage="currentLanguage"
      @setLang="(payload) => updateLanguage(payload)"
      @requestLogin="toggleLoginForm"
      @requestRegister="registerFormDisplay = !registerFormDisplay"
    ></header-component>
    <slider-component
      :store="store"
      :currentLanguage="currentLanguage"
    ></slider-component>
    <register-form-component
      class="register"
      :store="store"
      :currentLanguage="currentLanguage"
      :style="registerFormDisplay ? 'display: block' : 'display:none'"
      @regData="(payload) => apiRegisterData(payload)"
    ></register-form-component>
    <div class="info__btn"></div>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from 'vue';
import RegisterFormComponent from '../components/RegisterFormComponent.vue';
import HeaderComponent from '../components/HeaderComponent.vue';
import SliderComponent from '../components/SliderComponent.vue';
import { useLanguageStore } from '@/stores/languages';
const store = useLanguageStore();
const registerFormDisplay = ref(true);
// blurify start
const scrolly = ref();
const blur = ref('none');
const currentLanguage = ref('en');
const logEvent = () => {
  scrolly.value = window.top.scrollY;
  scrolly.value > 60 ? (blur.value = 'blur(7.5px)') : (blur.value = '');
};
onMounted(() => {
  document.addEventListener('scroll', (e) => logEvent(e));
});
onUnmounted(() => {
  document.removeEventListener('scroll', logEvent());
});
// blurify end
const apiRegisterData = (proxyData) => {
  console.log(proxyData);
};
const updateLanguage = (lang) => {
  currentLanguage.value = lang;
  console.log('selectedLang: ', lang);
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
    margin-top: 40px
    backdrop-filter: v-bind(blur)
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
    z-index: 144
    &:hover
      background: url('/src/assets/info_btn_hover.svg')
    &:active
      background: url('/src/assets/info_btn_active.svg')

@media (max-width: 1440px)
  .register
    right: 40px !important
  .info__btn
    right: 1% !important

@media (max-width: 980px)
  .register
    right: 20px !important

@media (max-width: 360px)
  .header
    margin: 0px !important
    background: linear-gradient(180deg, #000000 0%, rgba(0, 0, 0, 0) 100%)
  .register
    top: 340px !important
    top: 380px !important
    right: 15px !important
  .info__btn
    bottom: 5px !important
</style>
