<template>
  <div class="relative">
    <section id="sec1">
      <div class="bg_box"
        data-aos-once="false"
        data-aos="fade-down"
        data-aos-delay="0"
        data-aos-duration="500"
      ></div>
      <div
        data-aos-once="false"
        data-aos="zoom-in-left"
        data-aos-delay="0"
        data-aos-duration="500"
        class="deco0"
      >
        <img src="./S1/deco0.png" />
      </div>
      <div
        data-aos-once="false"
        data-aos="fade-down"
        data-aos-delay="0"
        data-aos-duration="1400"
        class="deco1"
      >
        <img src="./S1/deco1.png" />
      </div>
      <div
        data-aos-once="false"
        data-aos="fade-up"
        data-aos-delay="500"
        data-aos-duration="1400"
        class="deco2"
      >
        <img src="./S1/deco2.png" />
      </div>
      <S1_ani_deco class="ani_deco" />
      <div class="logo_box"
        data-aos-once="false"
        data-aos="fade-in"
        data-aos-delay="0"
        data-aos-duration="100"
      >
        <S1_ani_logo class="ani_logo" />
        <img v-if="!isMobile" class="sub_jp" src="./S1/sub_jp.png" />
        <img v-else class="sub_jp" src="./S1/sub_jp_mb.png" />
        <img v-if="!isMobile" class="sub" src="./S1/sub.png" />
        <img v-else class="sub" src="./S1/sub_mb.png" />
      </div>
    </section>
  </div>
</template>

<style lang="sass" scoped>
@import "src/assets/style/myvar"
@import ./sass/share
// --------------------------------
.deco0
  position: absolute
  right: 0vw
  top: 0vw
  // width: 30vw
  img
    height: 95vh
.deco1
  position: absolute
  right: 0
  top: -1.5vw
  width: 80vw
  img
    width: 100%
    height: 6vw
.deco2
  position: absolute
  left: 0
  bottom: -0.7vw
  width: 25vw
  img
    width: 100%
    height: 8vw
// --------------------------------
.bg_box
  height: 100%
  background:
    image: url(./S1/bg_pc.png)
    size: cover
    position: 50% 0
// --------------------------------
.ani_deco
  position: absolute
  transform: rotate(90deg)
  transform-origin: top left
  z-index: 999
// --------------------------------
.logo_box
  position: absolute
  top: 0
  right: 0
  bottom: 0
  left: 0
  margin: auto
  z-index: 1
  display: flex
  flex-direction: column
  justify-content: center
  align-items: center
  height: 100%

@media screen and (min-width: $bp-pc)
  #sec1
    height: 100vh
  .ani_logo
    width: 40vw
  .sub_jp
    width: 47vw
    margin:
      top: 5vw
      bottom: 4vw
  .sub
    width: 30vw
  // --------------------------------
  .ani_deco
    top: -10vw
    right: -45vw
    width: 40vw

@media screen and (max-width: $bp-mb)
  #sec1
    height: calc( 100vh - 63px )
  .ani_logo
    width: 70vw
    margin:
      top: 10vw
  .sub_jp
    width: 55vw
    margin:
      top: 9vw
      bottom: 8vw
  .sub
    width: 63vw
  // --------------------------------
  .deco1
    img
      height: 18vw
  .deco2
    width: 35vw
    img
      height: 40vw
  // --------------------------------
  .ani_deco
    top: -20vw
    right: -91vw
    width: 80vw

</style>

<script>
import S1_ani_logo from '@/projects/csyp/components/s1_ani_logo.vue'
import S1_ani_deco from '@/projects/csyp/components/s1_ani_deco.vue'
// @ is an alias to /src
import { isMobile } from '@/utils'
import $ from 'jquery'
export default {
  name: 'section1',
  components: {
    S1_ani_logo,
    S1_ani_deco
  },
  data() {
    return {
      isMobile
    }
  },

  methods: {},

  created() {},

  mounted() {},
  computed: {}
}
</script>
