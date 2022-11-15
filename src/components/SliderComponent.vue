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
    @slideChange="onSlideChange"
    class="mySwiper"
  >
    <swiper-slide
      ><div class="slide slider__one">
        <div class="slide__content">
          <div class="content__title">
            {{
              store.languages[currentLanguage].interface.slider.slides.first
                .title[0]
            }}
          </div>
          <div class="content__text">
            {{
              store.languages[currentLanguage].interface.slider.slides.first
                .body[0]
            }}
          </div>
        </div>
      </div> </swiper-slide
    ><swiper-slide
      ><div class="slide slider__two">
        <div class="slide__content">
          <div class="content__title">
            {{
              store.languages[currentLanguage].interface.slider.slides.second
                .title[0]
            }}
          </div>
          <div class="content__text">
            {{
              store.languages[currentLanguage].interface.slider.slides.second
                .body[0]
            }}
          </div>
          <div class="content__title">
            {{
              store.languages[currentLanguage].interface.slider.slides.second
                .title[1]
            }}
          </div>
          <div class="content__text">
            {{
              store.languages[currentLanguage].interface.slider.slides.second
                .body[1]
            }}
          </div>
          <div class="content__title">
            {{
              store.languages[currentLanguage].interface.slider.slides.second
                .title[2]
            }}
          </div>
          <div class="content__text">
            {{
              store.languages[currentLanguage].interface.slider.slides.second
                .body[2]
            }}
          </div>
        </div>
      </div> </swiper-slide
    ><swiper-slide
      ><div class="slide slider__three">
        <div class="slide__content">
          <div class="content__title">
            {{
              store.languages[currentLanguage].interface.slider.slides.third
                .title[0]
            }}
          </div>
          <div class="content__text">
            {{
              store.languages[currentLanguage].interface.slider.slides.third
                .body[0]
            }}
          </div>
        </div>
      </div>
    </swiper-slide>
  </swiper>
  <swiper
    :modules="modules"
    :slidesPerView="3"
    :direction="thumbsDirection"
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
            <div class="thumbs__head__content__title">
              {{
                store.languages[currentLanguage].interface.slider.pagination
                  .headers.sportsbook
              }}
            </div>
            <div class="thumbs__head__content__text">
              {{
                store.languages[currentLanguage].interface.slider.pagination
                  .body.sportsbook
              }}
            </div>
          </div>
        </div>
        <div
          @click="requestRedirect(store.links.bet_sportsbook)"
          class="thumbs__bottom"
        >
          {{
            store.languages[currentLanguage].interface.slider.pagination.buttons
              .sportsbook
          }}
        </div>
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
            <div class="thumbs__head__content__title">
              {{
                store.languages[currentLanguage].interface.slider.pagination
                  .headers.casino
              }}
            </div>
            <div class="thumbs__head__content__text">
              {{
                store.languages[currentLanguage].interface.slider.pagination
                  .body.casino
              }}
            </div>
          </div>
        </div>
        <div
          @click="requestRedirect(store.links.play_casino)"
          class="thumbs__bottom"
        >
          {{
            store.languages[currentLanguage].interface.slider.pagination.buttons
              .casino
          }}
        </div>
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
            <div class="thumbs__head__content__title">
              {{
                store.languages[currentLanguage].interface.slider.pagination
                  .headers.live_casino
              }}
            </div>
            <div class="thumbs__head__content__text">
              {{
                store.languages[currentLanguage].interface.slider.pagination
                  .body.live_casino
              }}
            </div>
          </div>
        </div>
        <div
          @click="requestRedirect(store.links.play_live_casino)"
          class="thumbs__bottom"
        >
          {{
            store.languages[currentLanguage].interface.slider.pagination.buttons
              .live_casino
          }}
        </div>
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
import { computed } from 'vue';

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  props: ['store', 'currentLanguage'],
  emits: ['requestRedirect'],
  setup(props, { emit }) {
    const thumbsSwiper = ref(null);
    const activeControl = ref('0');
    const thumbsDirection = computed(() => {
      return window.innerWidth <= 415 ? 'vertical' : 'horizontal';
    });
    const setThumbsSwiper = (swiper) => {
      thumbsSwiper.value = swiper;
    };
    const onSlideChange = (slideChange) => {
      activeControl.value = slideChange.activeIndex;
    };
    const requestRedirect = (where) => {
      emit('requestRedirect', where);
    };
    return {
      modules: [Autoplay, Pagination, Navigation, Thumbs],
      props,
      onSlideChange,
      thumbsSwiper,
      setThumbsSwiper,
      activeControl,
      thumbsDirection,
      requestRedirect,
    };
  },
};
</script>
<style scoped>
.swiper {
  width: 100%;
  height: 100vh;
}

.thumbs_swiper {
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
  justify-content: space-between;
  align-items: center;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  background-color: black;
  cursor: pointer;
  width: 459px;
  height: 176px;
  background: rgba(28, 35, 48, 0.63);
  border: 1.5px solid rgba(28, 35, 48, 0.63);
  border-radius: 30px;
  padding: 15px;
}
.thumb_swiper_slide-active {
  border: 1.5px solid #e49100;
  background-color: #0e1117;
}
.thumb_swiper_slide-active .thumbs__head__content__title {
  color: #e49100;
}
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
  min-height: 72px;
  min-width: 72px;
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
  text-align: left;
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 17px;
  letter-spacing: 0.01em;
  color: #ffffff;
}
.thumbs__icon__one {
  background-image: url('/src/assets/slider/sportsbook_icon.png');
}
.thumbs__icon__two {
  background-image: url('/src/assets/slider/casino_icon.png');
}
.thumbs__icon__three {
  background-image: url('/src/assets/slider/lifecasino_icon.png');
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

.mySwiper {
  min-height: 1234px;
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
  background-image: url('/src/assets/slider/slide_1.jpg');
}

.slider__two {
  background-image: url('/src/assets/slider/slide_2.jpg');
}

.slider__three {
  background-image: url('/src/assets/slider/slide_3.jpg');
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
  margin-left: 40px;
}

.content__title {
  font-weight: 600;
  font-size: 28px;
  line-height: 34px;
  margin-bottom: 15px;
  text-align: left;
}

.content__text {
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  font-weight: 900;
  font-size: 36px;
  line-height: 44px;
  text-align: left;
  margin-bottom: 45px;
  text-align: left;
}

@media (max-width: 1440px) {
  .slide__content {
    left: 0;
  }
  .thumbs_swiper {
    width: 100%;
    bottom: 1%;
  }
  .thumb_swiper_slide {
    min-height: 100%;
    max-width: 300px;
  }
}
@media (max-width: 980px) {
  .thumbs_swiper {
    bottom: 5%;
  }
  .thumb_swiper_slide {
    max-height: 160px;
    min-height: 100%;
    max-width: 260px;
    align-items: flex-end;
  }
  .thumbs__head__content__title {
    font-size: 16px;
    line-height: 20px;
  }
  .thumbs__head__content__text {
    font-size: 12px;
    line-height: 15px;
  }
  .slide {
    background-position: top;
  }
  .slide__content {
    max-width: 500px;
    margin-left: 20px;
  }
  .content__title {
    font-size: 24px;
    line-height: 29px;
  }
  .content__text {
    font-size: 36px;
    line-height: 44px;
  }
  .slider__one {
    background-image: url('/src/assets/slider/slide_1_mobile.jpg');
  }

  .slider__two {
    background-image: url('/src/assets/slider/slide_2_mobile.jpg');
  }

  .slider__three {
    background-image: url('/src/assets/slider/slide_3_mobile.jpg');
  }
}
@media (max-width: 415px) {
  .swiper {
    /* height: 100%; */
    height: 1280px;
  }
  .slider__one {
    background-position: top;
    background-image: url('/src/assets/slider/slide_1_mobile_long.jpg');
  }

  .slider__two {
    background-position: top;
    background-image: url('/src/assets/slider/slide_2_mobile_long.jpg');
  }

  .slider__three {
    background-position: top;
    background-image: url('/src/assets/slider/slide_3_mobile_long.jpg');
  }
  .thumbs_swiper {
    display: flex !important;
    flex-direction: column !important;
    bottom: 3%;
    height: calc(175px * 3);
    width: 100%;
    /* display: none !important; */
  }
  .thumbs_slide_container {
    margin-bottom: 0px;
  }
  .thumbs_slide_container:last {
    margin-bottom: none;
  }
  .slide__content {
    top: 115px;
    max-width: 320px;
  }
  .content__title {
    font-weight: 600;
    font-size: 16px;
    line-height: 20px;
    margin-bottom: 10px;
  }

  .content__text {
    font-weight: 900;
    font-size: 20px;
    line-height: 24px;
    text-align: left;
    margin-bottom: 25px;
  }
  .thumb_swiper_slide {
    max-height: 175px;
    max-width: 330px;
    align-items: center;
    padding: 20px 25px;
  }
  .thumbs__bottom {
    margin-left: 15%;
  }
}
</style>
