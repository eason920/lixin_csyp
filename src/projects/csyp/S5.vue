<template>
  <div class="relative">
    <section id="sec5">
      <div v-if="!isMobile" class="pc">
        <div
          data-aos-once="false"
          data-aos="fade-up"
          data-aos-delay="0"
          data-aos-duration="800"
        >
          <img src="./S5/pc.png" />
        </div>
        <div class="alt is1">61快速道路</div>
        <div class="alt">66快速道路</div>
      </div>
      <swiper v-else :options="swiperOption" ref="swiper2">
        <swiper-slide v-for="item in list" :key="'s' + item">
          <div class="alt">{{item}}</div>
        </swiper-slide>
      </swiper>
    </section>
  </div>
</template>

<script>
import $ from 'jquery'
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'

import { isMobile } from '@/utils'

export default {
  name: 'swiper-example-thumbs-gallery',
  title: 'Thumbs gallery with Two-way control',
  components: {
    Swiper,
    SwiperSlide
  },

  data() {
    return {
      vm: this,
      isMobile,
      list: [
        "66快速道路",
        "61快速道路",
      ],
      swiperOption: {
        loop: true,
        breakpoints: {
          768: {
            spaceBetween: 0
          },
          0: {
            spaceBetween: 0
          }
        },
        autoplay: {
          delay: 4000,
          disableOnInteraction: false
        },
        speed: 800,
        on: {
          slideChangeTransitionStart: function() {
            let eq = this.activeIndex
            if (eq >= 3) {
              eq = eq - 3
            }
            $('.dot3 li')
              .removeClass('active')
              .eq(eq)
              .addClass('active')
          }
        }
      }
    }
  },

  methods: {
    prevBtn() {
      this.$refs.swiper2.$swiper.slidePrev()
    },
    nextBtn() {
      this.$refs.swiper2.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      if (eq >= 3) {
        eq = eq - 3
      }
      this.$refs.swiper2.$swiper.slideTo(eq)
    }
  },

  created() {},

  mounted() {},

  computed: {}
}
</script>

<style lang="sass" scoped>
@import "src/assets/style/myvar"
@import ./sass/share
// ====================================
// == SWIPER v
// ====================================
// 圖片
@media screen and (max-width: $bp-mb)
  .swiper-slide
    background:
      position: 0 0
      size: contain
    position: relative

  .swiper-slide
    background:
      repeat: no-repeat
      position: left bottom
    &:nth-child(1), &:nth-child(3)
      background-image: url('./S5/mb1.png')

    &:nth-child(2), &:nth-child(4)
      background-image: url('./S5/mb2.png')

// ====================================
// == 架構
// ====================================
#sec5
  display: flex
  background-color: $db
.swiper-container
  z-index: 2

@media screen and (max-width: $bp-mb)
  #sec5
    flex-direction: column
  // h
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 88.3vw // w * 0.883

  // w
  .swiper-container
    width: 100vw

// ====================================
// == PIC
// ====================================
.alt
  position: absolute
  right: 3vw
  bottom: 2.5vw
  color: #fff
  font:
    size: 12px
    family: $ff
  letter-spacing: 3px
  text-shadow: 0px 2px 15px rgba(0, 0, 0, 0.7), 0px 2px 5px rgba(0, 0, 0, 0.5)
@media screen and (min-width: $bp-pc)
  .pc
    font-size: 0
    position: relative
    img
      width: 100%
    .is1
      right: auto
      left: 33vw
</style>
