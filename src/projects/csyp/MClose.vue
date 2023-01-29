<template>
  <div>
    <div id="lbMasker" v-if="bIsOpen" @click="toggleSidebar">
      <div class="lbMasker_box">
        <img class="deco3" src="./S1/deco3.png" />
        <img class="deco4" src="./S1/deco4.png" />
        <ul>
          <li
          data-aos="fade-up"
          :data-aos-delay="150 * i"
          :key="item.name"
          v-scroll-to="{
            element: `#${item.section}`,
            offset: item.offset ? item.offset : offset
          }"
          v-for="(item, i) in list"
          :class="[{back: i === 9}]"
          >
            <a href="#" @click.prevent="">{{ item.name }}</a>
          </li>
        </ul>
      </div>
    </div>
    <div id="lbswitch" v-if="!bIsOpen" @click="bIsOpen = !bIsOpen">
      <div class="lbswitch-wrapper">
        <div class="lbswitch-line is-tb"></div>
        <div class="lbswitch-line is-m"></div>
        <div class="lbswitch-line is-tb"></div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import { isMobile, isTablet } from '@/utils'
import navList from '@/info/navList'

export default {
  name: 'section1',

  data() {
    return {
      isMobile,
      isTablet,
      list: navList,
      bIsOpen: false
    }
  },

  methods: {
    toggleSidebar() {
      console.log('got fnb')
      this.bIsOpen = !this.bIsOpen
    }
  },

  created() {},

  mounted() {},

  computed: {
    offset() {
      if (this.isMobile) {
        return -39
      }

      if (this.isTablet) {
        return -45
      }

      return -56
    }
  }
}
</script>

<style lang="sass">
@import "src/assets/style/myvar"
@import ./sass/share

body.fixed
  overflow: hidden

#lbMasker
  position: fixed
  top: 0
  left: 0
  z-index: 99
  animation: start 1s linear forwards
  background-color: rgba(53,67,107,.95)
  .lbMasker_box
    height: 100%
    display: flex
    justify-content: center
    align-items: center
    position: relative
  ul
    position: relative
    z-index: 1
  li.back a
    color: $o
    border:
      style: solid
      width: 0 2px
      color: $o
    font-weight: 400
  a
    text-decoration: none
    display: block
    color: #fff
    letter-spacing: .5vw
    font:
      size: 20px
      family: $ff
      weight: lighter

.deco3, .deco4
  position: absolute
.deco3
  left: 0
  top: 0
.deco4
  right: 0
  bottom: 0

@keyframes start
  0%
    opacity: 0
  100%
    opacity: 1
//-------------
#lbswitch
  left: auto
  z-index: 100
  position: fixed
  top: 2.5vw
  left: 3.5vw
  width: 45px
  height: 45px
  cursor: pointer
  background-color: $o

.lbswitch-wrapper
  position: absolute
  top: 0
  bottom: 0
  right: 0
  left: 0
  display: flex
  justify-content: space-between
  margin: auto
  width: 35px
  height: 35px
  flex-direction: column

.lbswitch-line
  position: relative
  margin: auto
  width: 100%
  height: 1px
  background: rgba(255,255,255, 1)
  //
  transform: scaleX(1)
  opacity: 1
  transition: 1s

@media screen and (min-width: $bp-pc)
  #lbMasker
    width: 25vw
    height: 100vh
    li
      padding: 2.3vh 0

  .deco3, .deco4
    width: 60%

@media screen and (max-width: $bp-mb)
  #lbMasker
    bottom: 63px
    right: 0
    margin: auto
    li
      padding: 3vh 0
  .deco3, .deco4
    width: 45%

</style>
