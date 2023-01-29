<template>
  <div class="relative">
    <section id="sec2">
      <div class="text_box">
        <img class="float" src="./S2/deco.png" />
        <div
          data-aos-once="false"
          data-aos="fade-up"
          data-aos-delay="0"
          data-aos-duration="800"
          class="title"
        ><img src="./S2/title.png" /></div>
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
          >豐沃生活首環，<br/>食、衣、住、行一次滿足</h6>
          <p
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
          >約3分鐘大觀路成熟商圈，超強機能採買到位，7-11、全聯、億客城生鮮超市、路易莎、郵局等生活百貨等一應俱全，體現愜意的生活雅致。</p>
        </div>
        <ul class="dot2">
          <li
            v-for="item in 4"
            :key="'dot2' + item"
            @click="fnDotChange(item)"
          ></li>
        </ul>
      </div>
      <div class="pic_box">
        <div class="pre" @click="prevBtn"></div>
        <div class="nxt" @click="nextBtn"></div>
        <div class="pic_bg"></div>
        <swiper :options="swiperOption" ref="swiper2">
          <swiper-slide v-for="item in list" :key="'s' + item">
            <div class="alt">{{item}}</div>
          </swiper-slide>
        </swiper>
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
      list: ["全聯", "億客城生鮮超市", "水之丘公園","7-11"],
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
            if (eq >= 4) {
              eq = eq - 4
            }
            $('.dot2 li')
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
      if (eq >= 4) {
        eq = eq - 4
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
// == TEXT
// ====================================
.text_box
  display: flex
  flex-direction: column
  text-align: left
  font-family: $ff
  justify-content: center
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
    letter-spacing: .1vw
    line-height: 1.7

@media screen and (min-width: $bp-pc)
  .text_box
    padding: 0 9vw
  .title
    width: 8vw
  .line_outer
    width: 40px
    margin:
      top: 2vw
      bottom: 2vw
  .content
    margin-bottom: 1vw
    h6
      margin-bottom: 1vw

@media screen and (max-width: $bp-mb)
  .text_box
    padding: 10vw 10vw
  .title
    width: 32vw
  .line_outer
    width: 60px
    margin:
      top: 6vw
      bottom: 5vw
  .content
    margin-bottom: 1vw
    h6
      margin-bottom: 1vw

// --------------------------------
// FLOAT
@media screen and (min-width: $bp-pc)
  .text_box
    position: relative
    overflow: hidden
  .float
    position: absolute
    top: 2.5vw
    right: -12vw
    width: 27vw!important
    animation: ani 5s linear infinite
    transform: translateY(0px)

@keyframes ani
  0%
    transform: translateY(-5px)
  49%
    transform: translateY(5px)
  100%
    transform: translateY(-5px)

@media screen and (max-width: $bp-mb)
  .float
    display: none
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
  &:nth-child(1), &:nth-child(5)
    background-image: url('./S2/1.png')

  &:nth-child(2), &:nth-child(6)
    background-image: url('./S2/2.png')

  &:nth-child(3), &:nth-child(7)
    background-image: url('./S2/3.png')

  &:nth-child(4)
    background-image: url('./S2/4.png')

// ====================================
// == 架構
// ====================================
#sec2
  background:
    image: url('./S2/bg.png')
    size: cover
  display: flex
.text_box

.pic_box
  font-size: 0
  // overflow: hidden
.pic_bg
  position: absolute
  width: 102%
  height: 99%
  left: -0.7vw
  bottom: -0.3vw
  background:
    image: url(./S1/bg_pc.png)
    size: 100%
    position: 50% 0
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
  #sec2
    padding: 7vw 0
  .text_box
    width: 35vw
  .pic_box
    width: 65vw
  // h
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 42.795vw // w * 0.643

  // w
  .swiper-container
    width:  65vw

@media screen and (max-width: $bp-mb)
  #sec2
    flex-direction: column
    margin-bottom: 10vw
  // h
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 65.5vw // w * 2.87

  // w
  .swiper-container
    width: 100vw

  .pic_bg
    bottom: -2vw

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
  .pre, .nxt
    display: none

@media screen and (max-width: $bp-mb)
  $lr: 2vw
  .pre
    left: $lr

  .nxt
    right: $lr

// --------------------------------
// dot
$pl: 40px
@media screen and (min-width: $bp-pc)
  .dot2
    @include swiperCustomDot
    margin-left: 0
    width: 60px
@media screen and (max-width: $bp-mb)
  .dot2
    display: none

</style>
