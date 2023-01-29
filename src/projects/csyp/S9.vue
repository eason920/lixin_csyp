<template>
  <div class="relative">
    <section id="sec9">
      <img class="deco2" src="./S2/deco.png" />
      <img src="./S9/deco.png" class="float"/>
      <div class="pic_box"
        data-aos-once="false"
        data-aos="fade-up"
        data-aos-delay="0"
        data-aos-duration="800"
      >
        <div class="pre" @click="prevBtn"></div>
        <div class="nxt" @click="nextBtn"></div>
        <swiper :options="swiperOption" ref="swiper9">
          <swiper-slide v-for="item in list" :key="'s' + item">
            <div class="alt">{{item}}</div>
          </swiper-slide>
        </swiper>
      </div>
      <ul class="dot9">
        <li
          v-for="item in 3"
          :key="'dot9' + item"
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
      list: ["1111","2222","3333"],
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
            $('.dot9 li')
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
      this.$refs.swiper9.$swiper.slidePrev()
    },
    nextBtn() {
      this.$refs.swiper9.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      if (eq >= 3) {
        eq = eq - 3
      }
      this.$refs.swiper9.$swiper.slideTo(eq)
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
      background-image: url('./S9/pc1.png')

    &:nth-child(2), &:nth-child(5)
      background-image: url('./S9/pc2.png')

    &:nth-child(3), &:nth-child(6)
      background-image: url('./S9/pc3.png')
@media screen and (max-width: $bp-mb)
  .swiper-slide
    background-repeat: no-repeat
    &:nth-child(1), &:nth-child(4)
      background-image: url('./S9/mb1.png')

    &:nth-child(2), &:nth-child(5)
      background-image: url('./S9/mb2.png')

    &:nth-child(3), &:nth-child(6)
      background-image: url('./S9/mb3.png')

// ====================================
// == 架構
// ====================================
#sec9
  overflow: hidden
  background:
    color: $db
    size: cover
  display: flex

.pic_box
  font-size: 0
  margin: 0 auto
  // overflow: hidden
.alt
  position: absolute
  left: 2vw
  bottom: 1.5vw
  color: #fff
  font:
    size: 12px
    family: $ff
  letter-spacing: 3px
  text-shadow: 0px 2px 5px rgba(0, 0, 0, 0.5)

.swiper-container
  z-index: 2

@media screen and (min-width: $bp-pc)
  #sec9
    padding: 7vw 0

  // h
  .pic_box
    width: 80vw
    height: 42.6328vw // w * 0.53291
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 100%

  // w
  .swiper-container
    width:  100%

@media screen and (max-width: $bp-mb)
  #sec9
    flex-direction: column
    padding: 15vw 0
    // margin-bottom: 10vw
  // h
  .pic_box
    width: 80vw
    height: 132vw // w * 1.373
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 100%

  // w
  .swiper-container
    width:  100%

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
  $lr: -6vw
  .pre
    left: $lr

  .nxt
    right: $lr

// --------------------------------
// dot
.dot9
  @include swiperCustomDot
  position: absolute
  z-index: 2
  left: 50vw
  transform: translateX(-50%)
  width: 60px
  & li
    width: 12px
    height: 12px
    &.active
      background-color: #e89213
@media screen and (min-width: $bp-pc)
  .dot9
    bottom: 3vw
@media screen and (max-width: $bp-mb)
  .dot9
    bottom: 6vw

// --------------------------------
// FLOAT
.float
  position: absolute
  animation: ani1 5s linear infinite

@keyframes ani1
  0%
    transform: rotate(0deg)
  100%
    transform: rotate(359deg)

@media screen and (min-width: $bp-pc)
  .float
    width: 23vw!important
    top: -14vw
    left: 7vw

@media screen and (max-width: $bp-mb)
  .float
    width: 88vw!important
    top: -66vw
    left: -17vw
// --------------------------------
// FLOAT 2
.deco2
  position: absolute
  animation: ani2 5s linear infinite
  transform: translateY(0px)
@keyframes ani2
  0%
    transform: translateY(-5px)
  49%
    transform: translateY(5px)
  100%
    transform: translateY(-5px)
@media screen and (min-width: $bp-pc)
  .deco2
    width: 19vw!important
    bottom: -1.5vw
    right: -1vw

@media screen and (max-width: $bp-mb)
  .deco2
    width: 88vw!important
    bottom: -25vw
    right: -20vw
</style>
