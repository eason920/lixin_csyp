<template>
  <div class="relative">
    <section id="sec4">
      <div class="text_box">
        <div
          data-aos-once="false"
          data-aos="fade-up"
          data-aos-delay="0"
          data-aos-duration="800"
          class="title"
        ><img src="./S4/title.png" /></div>
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
          >9年教育一次到位，<br/>嬴在起跑點</h6>
          <p
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
          >[誠鑫一品] 坐落校園首排，約3分鐘草漯國小、草漯國中，人文氣質環繞輕盈上學，從小培養國際領袖的視野。</p>
        </div>
        <ul class="dot4">
          <li
            v-for="item in 2"
            :key="'dot4' + item"
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
      <div class="msg_box">
        <img src="./S5/deco.png" class="float"/>
        <div class="msg_wrapper">
          <div
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
            class="title2"
          >
            <img src="./S5/title.png" />
          </div>
          <div class="line_outer is2">
            <div class="line"
            data-aos-once="false"
            data-aos="fade-right"
            data-aos-delay="200"
            data-aos-duration="400"
            ></div>
          </div>
          <div class="content is2">
            <h6
              data-aos-once="false"
              data-aos="fade-up"
              data-aos-delay="0"
              data-aos-duration="800"
            >61、66快速道路，匯聚都會量能</h6>
            <p
              data-aos-once="false"
              data-aos="fade-up"
              data-aos-delay="0"
              data-aos-duration="800"
            >[誠鑫一品] 約7分鐘直上61、66快速道路，雙線串聯觀音、桃科、大潭三大工業區，15分鐘上國道2號、南來北往任你遊。</p>
          </div>
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
      list: [
        "草漯國中",
        "草漯國小"
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
            if (eq >= 2) {
              eq = eq - 2
            }
            $('.dot4 li')
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
      if (eq >= 2) {
        eq = eq - 2
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
    width: 42vw
  .line_outer
    width: 80px
    margin:
      top: 6vw
      bottom: 5vw
  .content
    margin-bottom: 1vw
    h6
      margin-bottom: 1vw

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
  &:nth-child(1), &:nth-child(3)
    background-image: url('./S4/1.jpg')

  &:nth-child(2), &:nth-child(4)
    background-image: url('./S4/2.jpg')
// ====================================
// == 架構
// ====================================
#sec4
  background:
    image: url('./S3/bg.png')
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
    color: rgba(255,255,255,.7)
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
  #sec4
    display: flex
    flex-wrap: wrap
  .text_box
    width: 35vw
  .pic_box
    width: 63vw
  // h
  .swiper-container, // height
  .swiper-wrapper,
  .swiper-slide
    height: 42.795vw // w * 0.643

  // w
  .swiper-container
    width:  65vw

@media screen and (max-width: $bp-mb)
  #sec4
    flex-direction: column
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
  .dot4
    @include swiperCustomDot
    margin-left: 0
    width: 30px
@media screen and (max-width: $bp-mb)
  .dot4
    display: none

// --------------------------------
// FLOAT
// msg box
.msg_box
  width: 100%
  background-color: $db
  position: relative
  &:before
    content: ""
    position: absolute
    top: 0
    right: 0
    bottom: 0
    left: 0
    margin: auto
    background:
      image: linear-gradient(to top,rgba(53,67,107,1) 65%, rgba(53,67,107,.5) 85%, rgba(53,67,107,0))
    z-index: 2
.msg_wrapper
  margin: 0 auto
  display: flex
  flex-direction: column
  align-items: center
  justify-content: center
  height: 100%
  position: relative
  z-index: 3
.float
  position: absolute
  animation: ani 5s linear infinite
  opacity: .5
.is2
  &.line_outer
    .line
      background-color: #fff
  &.content
    & > *
      color: #fff
.title2
  img
    width: 100%
@keyframes ani
  0%
    transform: rotate(0deg)
  100%
    transform: rotate(359deg)

@media screen and (min-width: $bp-pc)
  .msg_box
    margin-top: 10vw
    padding: 7vw 0 2vw
    .msg_wrapper
      width: 35vw
    .title2
      width: 25vw
  .float
    top: -14vw
    left: 18vw
    width: 30vw!important
  // --------------------------------
  .pic_box
    z-index: 1

@media screen and (max-width: $bp-mb)
  .msg_box
    z-index: 5
    margin-top: 15vw
    padding: 16vw 0 4vw
    .msg_wrapper
      width: 80vw
    .title2
      width: 76vw
  .float
    top: -34vw
    right: -30vw
    width: 60vw!important
</style>
