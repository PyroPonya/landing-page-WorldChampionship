<template>
  <swiper
    :spaceBetween="0"
    :centeredSlides="true"
    :autoplay="{
      delay: 5000,
      disableOnInteraction: false,
    }"
    :loop="false"
    :rewind="true"
    :pagination="false"
    :navigation="false"
    :modules="modules"
    :thumbs="{ swiper: thumbsSwiper }"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
    class="mySwiper"
  >
    <swiper-slide
      ><div class="slide slider__one">
        <div class="slide__content">
          <div class="content__title">Welcome bonus</div>
          <div class="content__text">10% NO RISK FREE BET UP TO 300 CAD</div>
          <div class="content__title">First deposit bonus</div>
          <div class="content__text">300% HUNTING BONUS UP TO 7,500 CAD</div>
        </div>
      </div> </swiper-slide
    ><swiper-slide
      ><div class="slide slider__two">
        <div class="slide__content">
          <div class="content__title">Welcome bonus</div>
          <div class="content__text">
            FOR NEW PLAYERS 3,5 BTC + 325 FS CASHBACK
          </div>
          <div class="content__title">RELOAD YOUE ACCOUNT</div>
          <div class="content__text">GET 50 FREE SPINS</div>
          <div class="content__title">VIP BONUS 110%</div>
          <div class="content__text">VIP UP TO 1500€</div>
        </div>
      </div> </swiper-slide
    ><swiper-slide
      ><div class="slide slider__three">
        <div class="slide__content">
          <div class="content__title">LIVE CASINO</div>
          <div class="content__text">
            EXPERIENCE REAL EMOTIONS IN HUNDREDS OF LIVE CASINO GAMES
          </div>
        </div>
      </div>
    </swiper-slide>
  </swiper>
  <swiper
    :modules="modules"
    :slidesPerView="3"
    :loop="false"
    watch-slides-progress
    @swiper="setThumbsSwiper"
    class="thumbs_swiper"
  >
    <swiper-slide class="thumbs_slide_container"
      ><div
        :class="activeControl == '0' ? 'thumb_swiper_slide-active' : ''"
        class="thumb_swiper_slide thumbs_swiper_one"
      >
        <div class="thumbs__head">
          <div class="thumbs__head__icon thumbs__icon__one"></div>
          <div class="thumbs__head__content">
            <div class="thumbs__head__content__title">SPORTBOOK</div>
            <div class="thumbs__head__content__text">
              Enjoy worlds biggest sports events
            </div>
          </div>
        </div>
        <div class="thumbs__bottom">BET</div>
      </div></swiper-slide
    >
    <swiper-slide class="thumbs_slide_container"
      ><div
        :class="activeControl == '1' ? 'thumb_swiper_slide-active' : ''"
        class="thumb_swiper_slide thumbs_swiper_two"
      >
        <div class="thumbs__head">
          <div class="thumbs__head__icon thumbs__icon__two"></div>
          <div class="thumbs__head__content">
            <div class="thumbs__head__content__title">CASINO</div>
            <div class="thumbs__head__content__text">
              Feel the excitement of the best games
            </div>
          </div>
        </div>
        <div class="thumbs__bottom">PLAY</div>
      </div></swiper-slide
    >
    <swiper-slide class="thumbs_slide_container"
      ><div
        :class="activeControl == '2' ? 'thumb_swiper_slide-active' : ''"
        class="thumb_swiper_slide thumbs_swiper_three"
      >
        <div class="thumbs__head">
          <div class="thumbs__head__icon thumbs__icon__three"></div>
          <div class="thumbs__head__content">
            <div class="thumbs__head__content__title">LIVE&nbsp;CASINO</div>
            <div class="thumbs__head__content__text">
              Experience the real casino thrill
            </div>
          </div>
        </div>
        <div class="thumbs__bottom">PLAY</div>
      </div></swiper-slide
    >
  </swiper>
</template>
<script>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';

// Import Swiper styles
import 'swiper/css';
import 'swiper/css/pagination';
import 'swiper/css/navigation';

// import required modules
import { Autoplay, Pagination, Navigation, Thumbs } from 'swiper';
import { ref } from 'vue';

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    const thumbsSwiper = ref(null);
    const activeControl = ref('0');
    const setThumbsSwiper = (swiper) => {
      thumbsSwiper.value = swiper;
    };
    const onSwiper = (swiper) => {
      console.log('onSwiper', swiper);
    };
    const onSlideChange = (slideChange) => {
      activeControl.value = slideChange.activeIndex;
    };
    return {
      modules: [Autoplay, Pagination, Navigation, Thumbs],
      onSwiper,
      onSlideChange,
      thumbsSwiper,
      setThumbsSwiper,
      activeControl,
    };
  },
};
</script>
<style scoped>
.swiper {
  width: 100%;
  height: 100%;
  height: 100vh;
}

.thumbs_swiper {
  /* display: none; */
  position: absolute;
  height: 200px;
  width: 85%;
  bottom: 40px;
}

.thumbs_slide_container {
  background-color: transparent !important;
  display: flex !important;
  align-items: center !important;
  justify-content: center !important;
}

.thumb_swiper_slide {
  width: 450px;
  height: 180px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  background-color: black;
  cursor: pointer;
  width: 459px;
  height: 176px;
  background: rgba(28, 35, 48, 0.63);
  border-radius: 30px;
}
/* @TODO: highlight current slide */
.thumb_swiper_slide-active {
  outline: 1.5px solid #e49100;
  background-color: #0e1117;
}
.thumb_swiper_slide-active .thumbs__head__content__title {
  color: #e49100;
}

/* .thumbs_swiper_one {
  background-image: url('/src/assets/slider/slide_2.jpg');
}

.thumbs_swiper_two {
  background-image: url('/src/assets/slider/slide_3.jpg');
}

.thumbs_swiper_three {
  background-image: url('/src/assets/slider/slide_1.jpg');
} */
.thumbs__head {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  gap: 24px;
}
.thumbs__head__icon {
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  height: 72px;
  width: 72px;
}
.thumbs__head__content {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 5px;
}
.thumbs__head__content__title {
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 700;
  font-size: 18px;
  line-height: 22px;
  letter-spacing: 0.01em;
  text-transform: uppercase;
  color: #ffffff;
}
.thumbs__head__content__text {
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 17px;
  letter-spacing: 0.01em;
  color: #ffffff;
}
.thumbs__icon__one {
  background-image: url('/src/assets/slider/sportsbook_logo.svg');
}
.thumbs__icon__two {
  background-image: url('/src/assets/slider/casino_logo.svg');
}
.thumbs__icon__three {
  background-image: url('/src/assets/slider/lifecasino_logo.svg');
}
.thumbs__bottom {
  height: 50px;
  width: 135px;
  background: linear-gradient(256.33deg, #ffb639 18.19%, #e49100 80.14%);
  border-radius: 14px;
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 700;
  font-size: 18px;
  line-height: 22px;
  letter-spacing: 0.01em;
  color: #1d232c;
  display: flex;
  align-items: center;
  justify-content: center;
}
.thumbs__bottom:hover {
  background: linear-gradient(256.33deg, #ffd644 18.19%, #ffbb0e 80.14%);
}
.thumbs__bottom:active {
  background: #13171e;
  color: #e49100;
}
.swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #fff;

  /* Center slide text vertically */
  display: -webkit-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  -webkit-justify-content: center;
  justify-content: center;
  -webkit-box-align: center;
  -ms-flex-align: center;
  -webkit-align-items: center;
  align-items: center;
}

/* .swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
} */

.mySwiper {
  margin-left: auto;
  margin-right: auto;
}

.slide {
  position: relative;
  width: 100%;
  height: 100%;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  background-color: black;
}

.slider__one {
  background-image: url('/src/assets/slider/slide_2.jpg');
}

.slider__two {
  background-image: url('/src/assets/slider/slide_3.jpg');
}

.slider__three {
  background-image: url('/src/assets/slider/slide_1.jpg');
}

.slide__content {
  position: absolute;
  left: 10%;
  top: 20%;
  max-width: 550px;
  letter-spacing: 0.01em;
  text-transform: uppercase;
  color: #ffffff;
  font-family: 'Montserrat';
  font-style: normal;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
  gap: 15px;
  margin-left: 40px;
}

.content__title {
  font-weight: 600;
  font-size: 30px;
  line-height: 37px;
}

.content__text {
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  font-weight: 900;
  font-size: 40px;
  line-height: 49px;
  text-align: left;
}
</style>
