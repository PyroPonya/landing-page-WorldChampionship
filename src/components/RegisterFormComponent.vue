<template>
  <div class="form">
    <div class="content">
      <div class="form__title">Welcome</div>
      <input
        v-model="dataBlob.mail"
        class="form__mail form__input"
        placeholder="E-mail"
      />
      <div class="pass-container">
        <input
          v-model="dataBlob.password"
          class="form__password form__input"
          placeholder="Password"
        />
        <div class="form__password-toggle"></div>
      </div>
      <div class="form__currency form__input"></div>
      <div class="form__country form__input"></div>
      <div class="form__text conditions">
        <div
          class="checkbox"
          :class="dataBlob.termsChecked ? 'checkbox-checked' : ''"
          @click="dataBlob.termsChecked = !dataBlob.termsChecked"
        ></div>
        <div class="terms__text">
          I am 18 years old and I accept the
          <a class="link">Privacy Policy</a>
          and
          <a class="link">Terms and Conditions*</a>
        </div>
      </div>
      <div class="form__text promos">
        <div
          class="checkbox"
          :class="dataBlob.promosChecked ? 'checkbox-checked' : ''"
          @click="dataBlob.promosChecked = !dataBlob.promosChecked"
        ></div>
        <div class="terms__text">Recive promos</div>
      </div>
      <div class="btn-container">
        <div class="form__btn">
          <div class="btn__text">SIGN&nbsp;UP</div>
        </div>
      </div>
      <div class="form__login">
        <div class="login__title">Already have an account?</div>
        <div class="login__link link">Sign In</div>
      </div>
    </div>
    <div class="form__partners"></div>
  </div>
</template>

<script>
import { ref, watchEffect } from 'vue';
export default {
  setup() {
    const termsChecked = ref(false);
    const promosChecked = ref(false);
    const dataBlob = ref({
      mail: '',
      password: '',
      CAD: '',
      country: '',
      termsChecked: false,
      promosChecked: false,
    });
    watchEffect(() => {
      console.log(dataBlob.value);
      console.log('mail: ', dataBlob.value.mail);
      console.log('pass: ', dataBlob.value.password);
      console.log('terms: ', dataBlob.value.termsChecked);
      console.log('promos: ', dataBlob.value.promosChecked);
    });
    return {
      termsChecked,
      promosChecked,
      dataBlob,
    };
  },
};
</script>

<style lang="sass" scoped>
.link
  background: linear-gradient(256.33deg, #FFB639 18.19%, #E49100 80.14%)
  background-clip: text
  text-fill-color: transparent
  -webkit-background-clip: text
  -webkit-text-fill-color: transparent
  cursor: pointer
.form
  background: #2B3446
  border-radius: 20px
  padding: 25px
  width: 400px
  min-height: 550px
  display: flex
  flex-direction: column
  .content
    padding: 25px
    padding-top: 0
  &__title
    display: flex
    justify-content: flex-start
    font-family: 'Montserrat'
    font-style: normal
    font-weight: 900
    font-size: 28px
    line-height: 34px
    text-align: center
    color: #FFFFFF
    margin-bottom: 14px
  &__input
    background: #1C2330
    border-radius: 12px
    font-family: 'Montserrat'
    font-style: normal
    font-weight: 600
    font-size: 14px
    line-height: 17px
    letter-spacing: 0.01em
    background: #1C2330
    border: none
    outline: none
    border-radius: 12px
    height: 50px
    width: 300px
    margin-bottom: 6px
    padding: 0 20px
    color: #FFFFFF
    &::placeholder
      color: #657083
  &__mail
  .pass-container
    position: relative
  &__password
    &-toggle
      position: absolute
      height: 10px
      width: 15px
      right: 20px
      bottom: 50%
      // background-color: #657083
      background-image: url('/src/assets/form/grey-eye.svg')
      cursor: pointer
  &__currency
    color: #FFFFFF
  &__country
    color: #FFFFFF
  &__text
    display: flex
    flex-direction: row
    align-items: center
    justify-content: flex-start
    gap: 8px
    margin: 10px 0px
    .checkbox
      border: 1px solid #B9C6D6
      outline: 1px solid #B9C6D6
      border-radius: 5px
      min-height: 20px
      min-width: 20px
      cursor: pointer
      &-checked
        border: 2px solid #2B3446
        border-radius: 2px
        min-height: 20px
        min-width: 20px
        position: relative
        background: #B9C6D6
        outline: 2px solid #B9C6D6
    .terms__text
      font-family: 'Montserrat'
      font-style: normal
      font-weight: 600
      font-size: 12px
      line-height: 15px
      align-items: center
      letter-spacing: 0.01em
      color: #B9C6D6
  &__mailing
  .btn-container
    background-color: #13171E
    border-radius: 12px
    // prevent selection start
    user-select: none
    -webkit-user-select: none
    -moz-user-select: none
    -khtml-user-select: none
    -ms-user-select: none
    // prevent selection end
  &__btn
    display: flex
    flex-direction: row
    justify-content: center
    align-items: center
    min-width: 300px
    min-height: 50px
    margin: 22px 0
    gap: 10px
    background: linear-gradient(256.33deg, #FFB639 18.19%, #E49100 80.14%)
    color: #13171E
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.25)
    border-radius: 12px
    cursor: pointer
    .btn__text
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
      background: linear-gradient(256.33deg, #FFB639 18.19%, #E49100 80.14%)
      -webkit-background-clip: text
      -webkit-text-fill-color: transparent
      background-clip: text
      text-fill-color: transparent

  &__login
    .login__title
      font-family: 'Montserrat'
      font-style: normal
      font-weight: 400
      font-size: 14px
      line-height: 17px
      letter-spacing: 0.01em
      color: #B9C6D6
    .login__link
      font-family: 'Montserrat'
      font-style: normal
      font-weight: 700
      font-size: 14px
      line-height: 17px
      text-decoration: underline
  &__partners
</style>
