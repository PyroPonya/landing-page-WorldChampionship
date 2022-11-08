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
    <div class="container__lang"></div>
  </div>
</template>

<script>
export default {
  setup() {
    return {};
  },
};
</script>

<style lang="sass" scoped>
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
  padding: 15px 5%
  //
  background-color: gray
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
    display: flex
    flex-direction: row
    gap: 15px
    //
    background-color: green
</style>
