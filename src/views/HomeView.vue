<template>
  <div class="container">
    <header-component
      class="header"
      :store="store"
      :currentLanguage="currentLanguage"
      @requestRedirect="(payload) => redirectTo(payload)"
      @setLang="(payload) => updateLanguage(payload)"
      @requestLogin="toggleLoginForm"
      @requestRegister="registerFormDisplay = !registerFormDisplay"
    ></header-component>
    <slider-component
      :store="store"
      :currentLanguage="currentLanguage"
      @requestRedirect="(payload) => redirectTo(payload)"
    ></slider-component>
    <register-form-component
      class="register"
      :store="store"
      :currentLanguage="currentLanguage"
      :style="registerFormDisplay ? 'display: flex' : 'display:none'"
      @requestRedirect="(payload) => redirectTo(payload)"
      @regData="(payload) => apiRegisterData(payload)"
    ></register-form-component>
    <!-- <div
      @click="store.useForm()"
      v-if="isMobile && store.showForm"
      class="bg__blur"
    ></div> -->
    <div @click="redirectTo(store.links.support)" class="info__btn"></div>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from 'vue';
import { useLanguageStore } from '@/stores/languages';
import RegisterFormComponent from '../components/RegisterFormComponent.vue';
import HeaderComponent from '../components/HeaderComponent.vue';
import SliderComponent from '../components/SliderComponent.vue';
const store = useLanguageStore();
// const isMobile = window.innerWidth <= 440 ? true : false;
const registerFormDisplay = ref(true);
// blurify start
const scrolly = ref();
const blur = ref('none');
const currentLanguage = ref('en');
const logEvent = () => {
  scrolly.value = window.top.scrollY;
  scrolly.value > 60 ? (blur.value = 'blur(7.5px)') : (blur.value = '');
};
// form background conditions start
const checkScreen = () => {
  window.innerWidth <= 440 ? store.useForm() : '';
};
//  form background conditions end

// autoshow form for mobiles start
function useTimeout(duration = 2000) {
  setTimeout(() => {
    if (store.showForm !== true) {
      store.useForm();
    } else {
      return null;
    }
  }, duration);
}
// autoshow form for mobiles end
onMounted(() => {
  document.addEventListener('scroll', (e) => logEvent(e));
  checkScreen();
  window.innerWidth <= 440 ? useTimeout(5000) : '';
});
onUnmounted(() => {
  document.removeEventListener('scroll', logEvent());
});
// blurify end
const redirectTo = (where) => {
  window.location.assign(where);
};
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
    backdrop-filter: v-bind(blur)
    -webkit-backdrop-filter: v-bind(blur)
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
  .bg__blur
    position: fixed
    left: 0
    top: 0
    height: 100vh
    width: 100vw
    background: rgba(0, 0, 0, 0.56)
    backdrop-filter: blur(4px)
    -webkit-backdrop-filter: blur(4px)
    z-index: 1

@media (max-width: 1440px)
  .register
    right: 40px !important
  .info__btn
    right: 1% !important

@media (max-width: 980px)
  .register
    right: 20px !important

@media (max-width: 440px)
  .header
    margin: 0px !important
    background: linear-gradient(180deg, #000000 0%, rgba(0, 0, 0, 0) 100%)
  .register
    top: 400px !important
    // right: 15px !important
    bottom: unset !important
    // left: 10% !important
    right: auto !important
    // position: fixed !important

  .info__btn
    bottom: 5px !important
</style>
