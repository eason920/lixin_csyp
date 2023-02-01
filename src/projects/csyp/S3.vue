<template>
  <div class="relative">
    <section id="sec3">
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
      <div class="text_box">
        <div class="float"
          data-aos-once="false"
          data-aos="fade-in"
          data-aos-delay="0"
          data-aos-duration="2000"
          v-if="!isMobile"
        >
          <img src="./S3/deco.png" />
        </div>
        <div
          data-aos-once="false"
          data-aos="fade-up"
          data-aos-delay="0"
          data-aos-duration="800"
          class="title"
        ><img src="./S3/title.png" /></div>
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
          >全齡樂活，<br/>收納為家的幸福藏品</h6>
          <p
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
          >高綠覆的怡然自得，8號親子公園在家旁，更奢享水之丘、風之谷雙主題公園；約2分鐘就到國際棒疊球場，滿足全家人的休閒育樂。</p>
        </div>
        <ul class="dot3">
          <li
            v-for="item in 3"
            :key="'dot3' + item"
            @click="fnDotChange(item)"
          ></li>
        </ul>
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
      list: [
        "水之丘公園",
        "草漯棒壘球場",
        "8號親子公園",
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
// == TEXT
// ====================================
.text_box
  display: flex
  flex-direction: column
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
  letter-spacing: 0.07em
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
    padding: 0 9vw
  .title
    width: 12vw
  .line_outer
    width: 60px
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
    width: 47vw
  .line_outer
    width: 80px
    margin:
      top: 6vw
      bottom: 5vw
  .content
    margin-bottom: 1vw
    h6
      margin-bottom: 1vw
    h6
      font-size: 4.5vw
    p
      font-size: 4vw

// --------------------------------
// FLOAT
@media screen and (min-width: $bp-pc)
  .text_box
    position: relative
    // overflow: hidden
  .float
    position: absolute
    top: 20vw
    right: -0vw
    width: 21vw!important
    // animation: ani 5s linear infinite
    transform: translateY(0px)
    img
      width: 100%

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
  background:
    repeat: no-repeat
    position: left bottom
  &:nth-child(1), &:nth-child(4)
    background-image: url('./S3/1.jpg')

  &:nth-child(2), &:nth-child(5)
    background-image: url('./S3/2.jpg')

  &:nth-child(3), &:nth-child(6)
    background-image: url('./S3/3.jpg')

// ====================================
// == 架構
// ====================================
#sec3
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
  bottom: -0.7vw
  background:
    color: #fff
    size: 100%
    position: 50% 0
.alt
  position: absolute
  right:1.3em
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
  #sec3
    padding: 7vw 0 11vw
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
  #sec3
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
  .text_box
    order: 1
  .pic_box
    order: 2

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
  .dot3
    @include swiperCustomDot
    margin-left: 0
    width: 50px
    li
     background-color: #fff
     box-shadow: 0 0 0.4vw #35436B66
@media screen and (max-width: $bp-mb)
  .dot3
    display: none

</style>
