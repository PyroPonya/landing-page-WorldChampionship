<template>
  <div class="container__header">
    <div class="container__logo">
      <div class="logo"></div>
      <div class="logo__title"></div>
    </div>
    <div class="container__nav">
      <div class="nav__element">SPORTSBOOK</div>
      <div class="nav__element">CASINO</div>
      <div class="nav__element">LIVE&nbsp;LAMES</div>
      <div class="nav__element">PROMOTIONS</div>
      <div class="nav__element">VIP&nbsp;PROGRAM</div>
    </div>
    <div class="container__btn">
      <div class="btn btn__login">SIGN&nbsp;IN</div>
      <div class="btn btn__register">SIGN&nbsp;UP</div>
    </div>
    <div
      :style="selectorOpen ? '--rotate: -135deg' : '--rotate: 45deg'"
      @click="selectorOpen = !selectorOpen"
      class="container__lang"
    >
      <div
        :style="`background: url(${avLang[selectedLang]})`"
        class="lang__logo"
      ></div>
      <div class="lang__title">{{ selectedLang }}</div>
      <div v-if="selectorOpen" class="lang__dropdown">
        <div
          @click="selectedLang = id"
          v-for="(el, id) in avLang"
          :key="id"
          class="dropdown__el"
        >
          <div
            :style="`background: url(${avLang[id]})`"
            class="lang__logo"
          ></div>
          <div class="lang__title">{{ id }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
export default {
  setup() {
    const selectorOpen = ref(false);
    const selectedLang = ref('EN');
    const avLang = {
      EN: '/src/assets/header/EN.svg',
      CA: '/src/assets/header/CA.svg',
      AU: '/src/assets/header/AU.svg',
      NZ: '/src/assets/header/NZ.svg',
      DE: '/src/assets/header/DE.svg',
      FR_CA: '/src/assets/header/FR_CA.svg',
    };
    console.log(avLang[selectedLang.value]);
    console.log(avLang);
    console.log(selectedLang.value);
    return {
      selectorOpen,
      avLang,
      selectedLang,
    };
  },
};
</script>

<style lang="sass" scoped>
$rotate: 45deg
$path: '/src/assets/header/EN.svg'
:root
  --rotate: 45deg
  --path: '/src/assets/header/EN.svg'
.container__header
  position: fixed
  top: 0px
  left: 0px
  display: flex
  flex-direction: row
  align-items: center
  justify-content: center
  gap: 5%
  width: 100%
  height: 60px
  padding: 0px 5%
  margin-top: 40px
  .container__logo
    display: flex
    flex-direction: row
    justify-content: center
    align-items: center
    min-width: 155px
    height: 52px
    background: url('/src/assets/header/logo.svg')
    background-position: center
    background-repeat: no-repeat
    cursor: pointer
  .container__nav
    display: flex
    flex-direction: row
    justify-content: center
    align-items: center
    gap: 20px
    .nav__element
      font-family: 'Montserrat'
      font-style: normal
      font-weight: 700
      font-size: 18px
      line-height: 22px
      letter-spacing: 0.01em
      color: #B9C6D6
      cursor: pointer
  .container__btn
    display: flex
    flex-direction: row
    gap: 15px
    .btn
      width: 140px
      height: 50px
      border-radius: 14px
      display: flex
      justify-content: center
      align-items: center
      cursor: pointer
    .btn__login
      border: 1.5px solid #B9C6D6
      font-family: 'Montserrat'
      font-style: normal
      font-weight: 700
      font-size: 18px
      line-height: 22px
      letter-spacing: 0.01em
      color: #B9C6D6
    .btn__register
      background: linear-gradient(256.33deg, #FFB639 18.19%, #E49100 80.14%)
      font-family: 'Montserrat'
      font-style: normal
      font-weight: 700
      font-size: 18px
      line-height: 22px
      letter-spacing: 0.01em
      color: #1D232C
  .container__lang
    position: relative
    display: flex
    flex-direction: row
    justify-content: center
    align-items: center
    gap: 15px
    padding: 10px 8px
    min-width: 130px
    height: 50px
    background: rgba(0, 0, 0, 0.6)
    border-radius: 10px
    cursor: pointer
    transition: all 0.3s ease-in-out
    .lang__logo
      background: url($path)
      background-position: center
      background-repeat: no-repeat
      height: 30px
      width: 50px
    .lang__title
      font-family: 'Montserrat'
      font-style: normal
      font-weight: 700
      font-size: 14px
      line-height: 114.7%
      color: #FFFFFF
      text-align: center
    &::after
      content: 'xxx'
      position: absolute
      height: 10px
      width: 10px
      border-right: 2px solid #ffffff
      border-bottom: 2px solid #ffffff
      right: 5%
      bottom: 45%
      transform: rotate(var(--rotate))
      transition: all 0.3s ease-in-out
    .lang__dropdown
      z-index: 122
      position: absolute
      display: flex
      flex-direction: column
      align-items: flex-start
      justify-content: center
      gap: 10px
      padding: 14px 8px
      min-width: 130px
      max-width: 130px
      top: 100%
      left: 10%
      border-radius: 10px
      background: rgba(0, 0, 0, 0.6)
      .dropdown__el
        cursor: pointer
        display: flex
        flex-direction: row
        justify-content: flex-start
        align-items: center
        gap: 15px
        min-width: 130px
        width: 100%
        height: 50px
        background: rgba(0, 0, 0, 0.6)
        color: #FFFFFF
</style>
