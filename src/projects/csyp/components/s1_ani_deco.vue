<template>
  <svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 236 110">
  <path class="st0" d="M2.2,36.4c104,78.1,188.5,95.3,156.7,34C106.7-30.1-19.2-10.3,132,74.8c81.1,45.7,83.5,15.9,24-41.2
    c-47.2-45.4-39.4-39,21,6.8c62.1,47.2,43.8,37.2,31.6,17.9c-12.3-19.3-5.6-45.8,11.5-25c19.3,23.5,5,2.1,13.8-3.9"/>
  </svg>
</template>

<style lang="sass" scoped>
.st0
  fill: none
  stroke: #FFF
  stroke-width: 3
  stroke-linecap: round
  stroke-dasharray: 1000
  stroke-dashoffset: 1000
  animation: letterDraw 7s ease-in-out forwards infinite

@keyframes letterDraw
  40%
    stroke-dashoffset: 0

  70%
    stroke-dashoffset: 0

  to
    stroke-dashoffset: -1000
</style>
