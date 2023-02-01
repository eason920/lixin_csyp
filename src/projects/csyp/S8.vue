<template>
  <div class="relative">
    <section id="sec8">
      <div class="pic_box"
        data-aos-duration="800"
      >
        <div class="pre" @click="prevBtn"></div>
        <div class="nxt" @click="nextBtn"></div>
        <swiper :options="swiperOption" ref="swiper8">
          <swiper-slide v-for="item in list" :key="'s' + item">
            <div class="alt">{{item}}</div>
          </swiper-slide>
        </swiper>
      </div>
      <ul class="dot8">
        <li
          v-for="item in 3"
          :key="'dot8' + item"
          @click="fnDotChange(item)"
        ></li>
      </ul>
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
  components: {
    Swiper,
    SwiperSlide
  },

  data() {
    return {
      vm: this,
      isMobile,
      list: ["222","3333","1111"],
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
            $('.dot8 li')
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
      this.$refs.swiper8.$swiper.slidePrev()
    },
    nextBtn() {
      this.$refs.swiper8.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      if (eq >= 3) {
        eq = eq - 3
      }
      this.$refs.swiper8.$swiper.slideTo(eq)
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
.swiper-slide
  background:
    position: 0 0
    size: contain
  position: relative
@media screen and (min-width: $bp-pc)
  .swiper-slide
    background-repeat: no-repeat
    &:nth-child(1), &:nth-child(4)
      background-image: url('./S8/pc1.jpg')

    &:nth-child(2), &:nth-child(5)
      background-image: url('./S8/pc1.jpg')

    &:nth-child(3), &:nth-child(6)
      background-image: url('./S8/pc1.jpg')
@media screen and (max-width: $bp-mb)
  .swiper-slide
    background-repeat: no-repeat
    &:nth-child(1), &:nth-child(4)
      background-image: url('./S8/mb1.jpg')

    &:nth-child(2), &:nth-child(5)
      background-image: url('./S8/mb1.jpg')

    &:nth-child(3), &:nth-child(6)
      background-image: url('./S8/mb1.jpg')

// ====================================
// == 架構
// ====================================
#sec8
  background:
    image: url('./S2/bg.jpg')
    size: cover
  display: flex

.pic_box
  font-size: 0
  // overflow: hidden
.alt
  position: absolute
  left: 1.3em
  bottom: 1.3em
  color: #fff
  font:
    size: 12px
    family: $ff
  letter-spacing: 0.06em
  text-shadow: 0px 2px 15px rgba(0, 0, 0, 0.7), 0px 2px 5px rgba(0, 0, 0, 0.5)
  
.swiper-container
  z-index: 2

@media screen and (min-width: $bp-pc)
  #sec8
    // padding:
    //   bottom: 7vw

  // h
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 56.25vw // w * 0.5625

  // w
  .swiper-container
    width:  100vw

@media screen and (max-width: $bp-mb)
  #sec8
    flex-direction: column
    // margin-bottom: 10vw
  // h
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 137.3vw // w * 1.373

  // w
  .swiper-container
    width: 100vw
// --------------------------------
// PRE NEX
.pic_box
  position: relative

.pre, .nxt
  display: block
  position: absolute
  width: .5em
  height: 1.55em
  font:
    size: 20px
  z-index: 3
  cursor: pointer
  background:
    size: contain
    repeat: no-repeat
  top: 50%
  transform: translateY(-50%)

.pre
  background:
    image: url("./S2/pre.png")

.nxt
  background:
    image: url("./S2/nxt.png")

@media screen and (min-width: $bp-pc)
  $lr: 2vw
  .pre
    left: $lr

  .nxt
    right: $lr

@media screen and (max-width: $bp-mb)
  $lr: 2vw
  .pre
    left: $lr

  .nxt
    right: $lr

// --------------------------------
// dot
.dot8
  @include swiperCustomDot
  position: absolute
  z-index: 2
  left: 50vw
  transform: translateX(-50%)
  width: 60px
  & li
    box-shadow: 0 0 0.4vw #0006
    &.active
      background-color: #e89213
@media screen and (min-width: $bp-pc)
  .dot8
    bottom: 2vw
@media screen and (max-width: $bp-mb)
  .dot8
    bottom: 6vw

</style>
