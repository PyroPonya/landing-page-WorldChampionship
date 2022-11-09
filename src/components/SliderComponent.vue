<template>
  <swiper
    :spaceBetween="0"
    :centeredSlides="true"
    :autoplay="{
      delay: 500000,
      disableOnInteraction: false,
    }"
    :loop="true"
    :pagination="false"
    :navigation="false"
    :modules="modules"
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
        </div>
        <div class="content__title">VIP BONUS 110%</div>
        <div class="content__text">VIP UP TO 1500€</div>
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
</template>
<script>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';

// Import Swiper styles
import 'swiper/css';
import 'swiper/css/pagination';
import 'swiper/css/navigation';

// import required modules
import { Autoplay, Pagination, Navigation } from 'swiper';

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  setup(props, { emit }) {
    const onSwiper = (swiper) => {
      console.log('onSwiper', swiper);
    };
    const onSlideChange = (slideChange) => {
      console.log(slideChange);
      emit('slideChange', slideChange.activeIndex);
    };
    return {
      modules: [Autoplay, Pagination, Navigation],
      onSwiper,
      onSlideChange,
    };
  },
};
</script>
<style scoped>
.swiper {
  width: 100%;
  height: 100%;
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

.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.swiper {
  margin-left: auto;
  margin-right: auto;
}

.slide {
  position: relative;
  width: 100%;
  height: 100%;
  background-position: contain;
  background-repeat: no-repeat;
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
