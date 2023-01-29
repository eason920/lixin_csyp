<template>
  <div class="relative">
    <section id="sec6">
      <div class="box">
        <div class="text_box">
          <div
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
            class="title"
          ><img src="./S6/title.png" /></div>
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
            >三心六線串聯北北桃，<br/>便捷通勤</h6>
            <p
              data-aos-once="false"
              data-aos="fade-up"
              data-aos-delay="0"
              data-aos-duration="800"
            >未來輕軌草漯支線接軌捷運，串聯桃園、中壢、航空城三大特區核心，同步南北台灣時尚生活，交通量能齊發，觀音前瞻國際！</p>
          </div>
          <ul class="dot2">
            <li
              v-for="item in 4"
              :key="'dot2' + item"
              @click="fnDotChange(item)"
            ></li>
          </ul>
        </div>
        <div class="pic_box" v-if="!isMobile">
          <p class="where">三心六線(截取自桃園市政府捷運工程局)</p>
          <div
            data-aos-once="false"
            data-aos="fade-up"
            data-aos-delay="0"
            data-aos-duration="800"
          >
            <img src="./S6/map.jpg" />
          </div>
        </div>
      </div>

      <!-- MB only -->
      <div v-if="isMobile" class="slider_box">
        <p class="where">三心六線(截取自桃園市政府捷運工程局)</p>
        <div id="slider">
          <div class="slider_pic">
            <img src="./S6/map.jpg" />
          </div>
        </div>
        <div id="fingerbox">
          <img class="finger" src="./S6/finger.png" />
        </div>
      </div>
    </section>
  </div>
</template>

<style lang="sass" scoped>
@import src/assets/style/myvar
@import ./sass/share
#sec6
  // height: 100vh
  background:
    color: #0059a9
.where
  position: absolute
  z-index: 3
  font:
    family: $ff
    weight: lighter
    size: 1vw
  letter-spacing: 1px
  color: #fff
  text-shadow: 0px 2px 15px rgba(0, 0, 0, 0.7), 0px 2px 5px rgba(0, 0, 0, 0.5)
@media screen and (min-width: $bp-pc)
  .pic_box
    position: relative
  .where
    top: 1vw
    left: 1vw
@media screen and (max-width: $bp-mb)
  #sec6
  .slider_box
    position: relative
    .where
      top: 4vw
      left: 4vw
      font:
        size: 3vw
  #slider
    overflow:
      x: scroll
      y: hidden
    height: 550 * 100vw / 375
    position: relative

  .slider_pic
    position: relative
    height: 100%
    img
      height: 100%

// --------------------------------
// FINGER BOX
#fingerbox
  @include fullScreen
  background:
    image: linear-gradient(to top, rgba(53,67,107,1), rgba(53,67,107,0) 50%)
  cursor: ew-resize
  transform: .3s
  &.on
    background: rgba(53,67,107,0)
    .finger
      opacity: 0

@media screen and (min-width: $bp-pc)
  .finger
    display: none
@media screen and (max-width: $bp-mb)
  .finger
    opacity: 1
    transform: .2s
    position: absolute
    bottom: 10vw
    width: 34vw
    transform: translateX(-50%)
    // animation: move 2s ease-in-out infinite alternate-reverse

// @keyframes move
//   0%
//     transform: translateX(0)
//   to
//     transform: translateX(-50%)

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
.line_outer
  overflow: hidden
  height: 1px
.line
  height: 100%
  width: 100%
  background-color: #fff
.content
  display: flex
  flex-direction: column
  & > *
    color: #fff
  h6
    font:
      size: 1.2vw
      family: $ff
    line-height: 1.5
  p
    font:
      size: 0.8vw
      family: $ff
    letter-spacing: .1vw
    line-height: 1.7

@media screen and (min-width: $bp-pc)
  .text_box
    padding:
      right: 9vw
  .title
    width: 13vw
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
    padding: 15vw 10vw 5vw
  .title
    width: 40vw
  .line_outer
    width: 60px
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

// ====================================
// == 架構
// ====================================
#sec6
  background:
    image: url('./S6/bg.jpg')
    size: cover
.box
  display: flex
.text_box

.pic_box
  font-size: 0

@media screen and (min-width: $bp-pc)
  #sec6
    // padding: 7vw 0
  .box
    padding: 7vw 10vw
  .text_box
    width: 35vw
  .pic_box
    // width: 65vw
    img
      width: 100%

@media screen and (max-width: $bp-mb)
  #sec6
    flex-direction: column
    // margin-bottom: 10vw

</style>

<script>
import $ from 'jquery'
// @ is an alias to /src
import { isMobile, isTablet } from '@/utils'

export default {
  name: 'section1',

  data() {
    return {
      isMobile,
      isTablet
    }
  },

  methods: {},

  created() {},

  mounted() {
    if (isMobile) {
      console.log('=========MB=========')
      const $doc = document.getElementById('slider')
      setTimeout(() => {
        let SL =  60 * $doc.offsetWidth / 100  // 位子換成%
        $doc.scrollLeft = SL

        let startX = 0
        $('#fingerbox').on('touchstart', e => {
          $('#fingerbox').addClass('on')

          if (startX === 0) {
            startX = e.targetTouches[0].pageX
          }
          console.log('touchstart', startX)
        })

        $('#fingerbox').on('touchmove', e => {
          let move = (e.targetTouches[0].pageX - startX) * -1
          switch (true) {
            case move <= -150:
              move = -150
              break
            case move >= 150:
              move = 150
              break
            default:
          }
          $doc.scrollLeft = SL + move
        })

        $('#fingerbox').on('touchend', e => {
          $('#fingerbox').remove()
        })
      }, 1000)
    }
  },

  computed: {}
}
</script>
