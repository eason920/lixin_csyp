<template>
  <div class="home no-padding-top">
    <Loading :loading="load" />
    <!-- <SideNavigation v-if="isSide" /> -->
    <!-- <Navigation v-if="!isMobile" /> -->
    <MClose />
    <!-- <Indigator :viewIndex="viewIndex" /> -->
    <!-- <full-page
      ref="fullPage"
      :options="options"
      id="fullpage"
    > -->
    <vue-lazy-component class="section" id="section1" @init="init">
      <S1 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section2" @init="init">
      <S2 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section3" @init="init">
      <S3 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section4" @init="init">
      <S4 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section5" @init="init">
      <S5 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section6" @init="init">
      <S6 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section7" @init="init">
      <S7 />
    </vue-lazy-component>
    <!--vue-lazy-component class="section" id="section8" @init="init">
      <S8 />
    </vue-lazy-component>
    <vue-lazy-component class="section" id="section9" @init="init">
      <S9 />
    </vue-lazy-componen-->
    <vue-lazy-component class="section" id="contact">
      <ContactSection />
    </vue-lazy-component>
    <!-- ======================== -->
    <MobileNav />
  </div>
</template>

<script>
// @ is an alias to /src
import $ from 'jquery'
import Navigation from '@/layouts/Navigation.vue'
import { isMobile } from '@/utils'
import SideNavigation from '@/layouts/SideNavigation.vue'
import ContactSection from '@/layouts/ContactSection.vue'
import MobileNav from '@/layouts/MobileNav.vue'
import Loading from '@/components/Loading.vue'
// import Indigator from '@/components/Indigator.vue'
// import SwiperDemo from '@/projects/csyp/swiperDemo_S7_single.vue'
import MClose from '@/projects/csyp/MClose.vue'
import S1 from '@/projects/csyp/S1.vue'
import S2 from '@/projects/csyp/S2.vue'
import S3 from '@/projects/csyp/S3.vue'
import S4 from '@/projects/csyp/S4.vue'
import S5 from '@/projects/csyp/S5.vue'
import S6 from '@/projects/csyp/S6.vue'
import S7 from '@/projects/csyp/S7.vue'
import S8 from '@/projects/csyp/S8.vue'
import S9 from '@/projects/csyp/S9.vue'
export default {
  name: 'home',
  components: {
    Loading,
    // Indigator,
    Navigation,
    SideNavigation,
    ContactSection,
    MobileNav,
    // SwiperDemo,
    MClose,
    S1,
    S2,
    S3,
    S4,
    S5,
    S6,
    S7,
    S8,
    S9,
  },

  data() {
    return {
      isMobile,
      load: true,
    }
  },
  created() {
    $(document).ready(() => {
      // Images loaded is zero because we're going to process a new set of images.
      var imagesLoaded = 0
      // Total images is still the total number of <img> elements on the page.
      var totalImages = $('img').length

      const allImagesLoaded = () => {
        this.load = false
      }
      const imageLoaded = () => {
        imagesLoaded++
        if (imagesLoaded === totalImages) {
          allImagesLoaded()
        }
      }
      $('img').each(function(idx, img) {
        $('<img>')
          .on('load', imageLoaded)
          .attr('src', $(img).attr('src'))
      })
    })
  },
  mounted() {

  },
  methods: {
    init() {}
  }
}
</script>

<style lang="sass">
@import "src/assets/style/myvar"

</style>

<style lang="sass">
// @import url('https://fonts.googleapis.com/css?family=Noto+Serif+TC')
@import "src/assets/style/myvar"
*
 // font-family: "Noto Serif TC", serif !important
 // letter-spacing: 1px
  // Noto Sans CJK TC  粗細Regular 400
  // Noto Serif CJK TC  粗細Regular 400  Bold 700
.wave
  position: absolute
.wave_l1, .wave_l2
  left: 0
.wave_r1, .wave_r2
  right: 0
section
  // overflow: visible
  position: relative

</style>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Playball&display=swap');
@import '../assets/style/variableColor.scss';

.section,
.section .fp-slide,
.section .fp-tableCell {
  height: auto !important;
}


</style>
