<template>
  <div class="main-section">
    <div class="text">
      <h1>Join the Toptal Leaders</h1>
      <p>
        Join the ranks of an ever-growing international community through hosting
        exclusive events, attending popular conferences and seminars, and crafting
        widely-shared content. The Toptal Leaders are the driving force in expanding
        the Toptal network by creating unique experiences and locating the most 
        exceptional talent.
      </p>
    </div>
    <div 
      class="carousel"
      @mouseenter="isScrolling = false"
      @mouseout="isScrolling = true"
    >
      <div
        v-for="(image, idx) in images"
        :key="idx"
        :class="[
          'carousel-image-container',
          getSizeClass(idx)
        ]"
        :style="getStyle(idx)"
      />
    </div>
  </div>
</template>

<script>
import images from '../content-data/carousel-images.js'

// The constants must be the same as the css variables
const CAROUSEL_HEIGHT = 200
// const IMAGE_STD_WIDTH = 400
const GROUP_WIDTH = 800
const CAROUSEL_MOVEMENT_X = -0.2
const CAROUSEL_MOVEMENT_T = 1

const imageSizes = [
  'regular',
  'small-top',
  'small-bottom',
  'square',
]
const leftPositions = [
  0,
  400, 
  400,
  600
]

export default {
  data(){
    let temp = []
    let minImageCount = imageSizes.length * (images.length * 2 + 1)
    while(temp.length < minImageCount) temp.push(...images)

    return {
      isScrolling: true,
      images: temp,
      dy: 0
    }
  },
  computed: {
    compDY(){
      return this.dy
    }
  },
  methods: {
    getSizeClass(n){
      return imageSizes[n%imageSizes.length]
    },
    getStyle(n){
      // figuring out the position
      const group = Math.floor(n / imageSizes.length)
      const order = n % imageSizes.length

      const left = leftPositions[order] + GROUP_WIDTH * group + this.compDY + 'px'
      const top = (order === 2 ? CAROUSEL_HEIGHT / 2 : 0)  + 'px';
      const backgroundImage = `url('${this.images[n].src}')`

    return {
        left,
        top,
        backgroundImage
      }
    }
  },
  mounted(){
    setInterval(() => {
      if(this.isScrolling) this.dy = (this.dy + CAROUSEL_MOVEMENT_X) % (GROUP_WIDTH * images.length)
      // console.log(this.dy)
    }, CAROUSEL_MOVEMENT_T);
  }
}
</script>

<style lang="scss" scoped>
@import '../styles/global.scss';
.text {
  max-width: $screen9;
  margin: auto;
  text-align: justify;
  color: $bw-gradient4;
  h1 {
    text-align: center;
    color: $blue0;
    font-size: 2.5rem;
  }
}

$carousel-height: 200px;
$image-std-width: 400px;
$image-margin: 2.5px;

.carousel {
  height: $carousel-height;
  margin: 100px 0;
  overflow: hidden;
  border-radius: 5px;
} 

.carousel-image-container {
  border-radius: 5px;
  overflow: hidden;
  margin: 0 2.5px;
  @extend %dead-center;
  position: absolute;
  background-position: center center;
  background-size: cover;
  filter: grayscale(1);
  &:hover {
    filter: grayscale(0);
  }
  &.regular {
    height: 100%;
    width: 400px - $image-margin * 2;
  }
  &.small-top, &.small-bottom {
    height: $carousel-height / 2 - $image-margin;
    width: $image-std-width / 2 - $image-margin * 2;
  }
  &.small-top {
    margin-bottom: $image-margin;
  }
  &.small-bottom {
    margin-top: $image-margin;
  }
  &.square {
    width: $carousel-height - $image-margin * 2;
    height: $carousel-height;
  }
}

.carousel-image-container img{
  width: 100%;
}

</style>
