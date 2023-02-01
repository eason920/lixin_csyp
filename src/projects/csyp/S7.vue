<template>
  <div class="relative">
    <section id="sec7">
      <img class="deco1" src="./S7/deco1.png" />
      <img class="deco2" src="./S7/deco2.png" />
      <div v-if="isMobile" class="slide_box"
        data-aos-once="false"
        data-aos="fade-up"
        data-aos-delay="0"
        data-aos-duration="800"
      >
        <div class="pre" @click="prevBtn"></div>
        <div class="nxt" @click="nextBtn"></div>
        <swiper :options="swiperOption" ref="swiper7">
          <swiper-slide v-for="item in 3" :key="'s' + item" />
        </swiper>
      </div>
      <div v-else class="pic_box"
        data-aos-once="false"
        data-aos="fade-up"
        data-aos-delay="0"
        data-aos-duration="800"
      >
        <img src="./S7/1.jpg" />
        <img src="./S7/2.jpg" />
        <img src="./S7/3.jpg" />
      </div>
      <div class="text_box">
        <div
          data-aos-once="false"
          data-aos="fade-up"
          data-aos-delay="0"
          data-aos-duration="800"
          class="title"
        ><img src="./S7/title.png" /></div>
        <div class="line_outer">
          <div class="line"
          data-aos-once="false"
          data-aos="fade-right"
          data-aos-delay="200"
          data-aos-duration="400"
          ></div>
        </div>
        <div class="content">
          <h6
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
          >深耕桃園近30年，書寫家的唯一</h6>
          <p
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
          >【誠鑫建設】慧眼選地，在最好的地段蓋最好的建築；精工細琢，追求創新，更擁有一顆融入在地的心，實現土地的最高價值。</p>
        </div>
      </div>
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
      list: [],
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
          }
        }
      }
    }
  },

  methods: {
    prevBtn() {
      this.$refs.swiper7.$swiper.slidePrev()
    },
    nextBtn() {
      this.$refs.swiper7.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      if (eq >= 3) {
        eq = eq - 3
      }
      this.$refs.swiper7.$swiper.slideTo(eq)
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
// == TEXT
// ====================================
.text_box
  display: flex
  flex-direction: column
  font-family: $ff
  justify-content: center
  align-items: center
  position: relative
  z-index: 1
  img
    width: 100%
.title
.line_outer
  overflow: hidden
  height: 1px
.line
  height: 100%
  width: 100%
  background-color: $db
.content
  display: flex
  flex-direction: column
  letter-spacing: 0.07em
  text-align: center
  h6
    color: #666
    font:
      size: 1.2vw
      family: $ff
    line-height: 1.5
  p
    color: #111
    font:
      size: 0.8vw
      family: $ff
    line-height: 1.7

@media screen and (min-width: $bp-pc)
  .text_box
    padding: 2vw 9vw 0
  .title
    width: 20vw
  .line_outer
    width: 40px
    margin:
      top: 0.5vw
      bottom: 0.8vw
  .content
    margin-bottom: 1vw
    h6
      margin-bottom: 1vw

@media screen and (max-width: $bp-mb)
  .text_box
    padding: 7vw 12vw 12vw
  .title
    width: 70vw
  .line_outer
    width: 100px
    margin:
      top: 3vw
      bottom: 5vw
  .content
    margin-bottom: 1vw
    h6
      margin-bottom: 1vw
    h6
      font-size: 4.5vw
    p
      font-size: 4vw

// ====================================
// == SWIPER v
// ====================================

// 圖片
.swiper-slide
  background:
    position: 0 0
    size: contain
  position: relative

.swiper-slide
  background-repeat: no-repeat
  &:nth-child(1), &:nth-child(4)
    background-image: url('./S7/1.jpg')

  &:nth-child(2), &:nth-child(5)
    background-image: url('./S7/2.jpg')

  &:nth-child(3), &:nth-child(6)
    background-image: url('./S7/3.jpg')

// ====================================
// == 架構
// ====================================
#sec7
  background:
    image: url('./S2/bg.jpg')
    size: cover
  display: flex
  flex-direction: column
.slide_box
  font-size: 0
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
  #sec7
    padding: 7vw 0 5vw
  .text_box
    width: 50vw
    margin: 0 auto

@media screen and (max-width: $bp-mb)
  #sec7
    // margin-bottom: 10vw
  .slide_box
    width: 80vw
    margin: 17vw auto 0
    height: 86.8vw // w * 1.08527
  // h
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 100%

  // w
  .swiper-container
    width: 100%

// --------------------------------
// PRE NEX
.slide_box
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
    image: url("./S7/pre.png")

.nxt
  background:
    image: url("./S7/nxt.png")

@media screen and (min-width: $bp-pc)
  .pre, .nxt
    display: none

@media screen and (max-width: $bp-mb)
  $lr: -6vw
  .pre
    left: $lr

  .nxt
    right: $lr

// --------------------------------
// PIC BOX
@media screen and (min-width: $bp-pc)
  .pic_box
    width: 80vw
    margin: auto
    display: flex
    justify-content: space-between
    & > *
      width: 26vw

// --------------------------------
// DECO
.sec7
  position: relative
.deco1, .deco2
  position: absolute
  bottom: 0
.deco1
  left: 0
.deco2
  right: 0
@media screen and (min-width: $bp-pc)
  .deco1
    width: 30vw
  .deco2
    width: 22vw
@media screen and (max-width: $bp-mb)
  .deco1
    width: 50vw
  .deco2
    width: 50vw
    right: -10vw
</style>
