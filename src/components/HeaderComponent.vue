<template>
  <div class="container__header">
    <div class="container__logo">
      <div
        @click="mobileMenuOpen = !mobileMenuOpen"
        :class="mobileMenuOpen ? 'container__nav-mobile-active' : ''"
        class="container__nav-mobile"
      >
        <div v-if="mobileMenuOpen" class="mobile__background">
          <div class="nav__mobile">
            <div
              @click.stop="requestRedirect('SPORTSBOOK')"
              class="nav__mobile__element"
            >
              SPORTSBOOK
            </div>
            <div
              @click.stop="requestRedirect('CASINO')"
              class="nav__mobile__element"
            >
              CASINO
            </div>
            <div
              @click.stop="requestRedirect('LIVE GAMES')"
              class="nav__mobile__element"
            >
              LIVE&nbsp;GAMES
            </div>
            <div
              @click.stop="requestRedirect('PROMOTIONS')"
              class="nav__mobile__element"
            >
              PROMOTIONS
            </div>
            <div
              @click.stop="requestRedirect('VIP PROGRAM')"
              class="nav__mobile__element"
            >
              VIP&nbsp;PROGRAM
            </div>
          </div>
        </div>
      </div>
      <div class="logo"></div>
    </div>
    <div class="container__nav">
      <div class="nav__element">SPORTSBOOK</div>
      <div class="nav__element">CASINO</div>
      <div class="nav__element">LIVE&nbsp;GAMES</div>
      <div class="nav__element">PROMOTIONS</div>
      <div class="nav__element">VIP&nbsp;PROGRAM</div>
    </div>
    <div class="container__btn">
      <div @click="requestLogin" class="btn btn__login">SIGN&nbsp;IN</div>
      <div @click="requestRegister" class="btn btn__register">SIGN&nbsp;UP</div>
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
          @click="setLanguage(id)"
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
import CA_svg from '/src/assets/header/CA.svg';
import EN_svg from '/src/assets/header/EN.svg';
import AU_svg from '/src/assets/header/AU.svg';
import NZ_svg from '/src/assets/header/NZ.svg';
import DE_svg from '/src/assets/header/DE.svg';
import FR_CA_svg from '/src/assets/header/FR_CA.svg';
export default {
  setup(props, { emit }) {
    const selectorOpen = ref(false);
    const selectedLang = ref('EN');
    const mobileMenuOpen = ref(false);
    const avLang = {
      CA: CA_svg,
      EN: EN_svg,
      AU: AU_svg,
      NZ: NZ_svg,
      DE: DE_svg,
      FR_CA: FR_CA_svg,
    };
    const setLanguage = (id) => {
      selectedLang.value = id;
      emit('setLang', selectedLang.value);
    };
    const requestLogin = () => {
      emit('requestLogin');
    };
    const requestRegister = () => {
      emit('requestRegister');
    };
    const requestRedirect = (where) => {
      console.log('redirect to: ', where);
    };
    return {
      selectorOpen,
      avLang,
      selectedLang,
      mobileMenuOpen,
      setLanguage,
      requestLogin,
      requestRegister,
      requestRedirect,
    };
  },
};
</script>

<style lang="sass" scoped>
$rotate: 45deg
:root
  --rotate: 45deg
.container__header
  position: fixed
  top: 0px
  left: 0px
  display: flex
  flex-wrap: wrap
  flex-direction: row
  align-items: center
  justify-content: space-between
  gap: 5%
  width: 100%
  height: 60px
  padding: 0 5%
  margin-top: 40px
  .container__logo
    display: flex
    flex-direction: row
    justify-content: center
    align-items: center
    gap: 20px
    .container__nav-mobile
      position: relative
      display: none
      height: 10px
      width: 10px
      border-bottom: 3px solid #B9C6D6
      z-index: 146
      transition: all 0.3s ease-in-out
      cursor: pointer
      margin: 5px
      &::before
        position: absolute
        top: 0px
        left: 0
        content: ''
        border-bottom: 3px solid #B9C6D6
        height: 20px
        width: 20px
        transition: all 0.3s ease-in-out
      &::after
        position: absolute
        top: -3px
        left: 0
        content: ''
        border-top: 3px solid #B9C6D6
        height: 20px
        width: 20px
        transition: all 0.3s ease-in-out
      &:active
        border-color: #e49100
      &:active::before
        border-color: #e49100
      &:active::after
        border-color: #e49100
      &-active
        border: none
        &::before
          transform: rotateZ(45deg)
          top: -8px
          left: 0px
        &::after
          transform: rotateZ(-45deg)
          top: 4px
          left: 0px
      .mobile__background
        z-index: -1
        position: fixed
        top: 0
        left: 0
        width: 100vw
        height: 100vh
        background: rgba(0, 0, 0, 0.82)
        background-position: center
        background-size: cover
        .nav__mobile
          display: flex
          flex-direction: column
          justify-content: flex-start
          align-items: flex-start
          gap: 20px
          padding: 110px 20px
          &__element
            font-weight: 700
            font-size: 18px
            line-height: 22px
            letter-spacing: 0.01em
            color: #B9C6D6
            min-width: 250px
            min-height: 35px
            display: flex
            justify-content: flex-start
            align-items: center
            padding: 8px 40px
            &:active
              background: #000000
              border-radius: 20px
              color: #E49100
    .logo
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
      &:hover
        color: #F1F1F1
      &:active
        background: linear-gradient(256.33deg, #FFB639 18.19%, #E49100 80.14%)
        -webkit-background-clip: text
        -webkit-text-fill-color: transparent
        background-clip: text
        text-fill-color: transparent
        border-bottom: 1px solid #E49100
        margin-bottom: -1px
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
      // prevent selection start
      user-select: none
      -webkit-user-select: none
      -moz-user-select: none
      -khtml-user-select: none
      -ms-user-select: none
      // prevent selection end
    .btn__login
      border: 1.5px solid #B9C6D6
      font-family: 'Montserrat'
      font-style: normal
      font-weight: 700
      font-size: 18px
      line-height: 22px
      letter-spacing: 0.01em
      color: #B9C6D6
      &:hover
        border: 1.5px solid #F1F1F1
        color: #F1F1F1
      &:active
        border: 1.5px solid #E49100
        color: #E49100
    .btn__register
      background: linear-gradient(256.33deg, #FFB639 18.19%, #E49100 80.14%)
      font-family: 'Montserrat'
      font-style: normal
      font-weight: 700
      font-size: 18px
      line-height: 22px
      letter-spacing: 0.01em
      color: #1D232C
      &:hover
        background: linear-gradient(256.33deg, #FFD644 18.19%, #FFBB0E 80.14%)
      &:active
        background: #13171E
        color: #E49100
  .container__lang
    position: relative
    display: flex
    flex-direction: row
    justify-content: flex-start
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
      content: ''
      position: absolute
      height: 10px
      width: 10px
      border-right: 2px solid #ffffff
      border-bottom: 2px solid #ffffff
      right: 10%
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
        color: #FFFFFF
@media (max-width: 1440px)
  .container__header
    // flex-wrap: nowrap
    gap: unset
    padding: 0 40px
  .nav__element
    font-size: 15px !important
  .lang__dropdown
    left: 0% !important
    .dropdown__el
      min-width: 100% !important
@media (max-width: 960px)
  .container__header
    padding: 0 20px
  .container__logo
    margin-right: 250px
    .logo
      z-index: 146
  .container__nav
    display: none !important
  .container__nav-mobile
    display: flex !important
@media (max-width: 360px)
  .container__header
    flex-wrap: nowrap
  .container__logo
    margin-right: 0px
  .logo
    background: url('/src/assets/header/logo_mobile.svg') !important
    max-height: 50px !important
    max-width: 50px !important
    background-position: left !important
    background-repeat: no-repeat !important
  .container__btn
    display: none !important
</style>
