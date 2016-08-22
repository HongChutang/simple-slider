<template>
<div class="slider" @mouseover = "pause && pausePlay()" @mouseout = "pause && goPlay()">
  <ul :style="{'width': `${this.count * 100}%`, 'left': `${-100 * this.current}%`, transitionDuration: `${this.speed}s`}">
    <li class="slider-item" v-for="item in items" :style="{'width': `${100 / this.count}%`}">
      <a v-link="{path: item.link}" :style="'width': 100%"><img :src="item.src", :alt="item.alt" :style="'width': 100%"></a>
    </li>
  </ul>
  <slider-dots v-if="dots", :count="count", :current="current", :turn="turn"></slider-dots>
  <slider-arrows v-if="arrows", :turn="turn"></slider-arrows>
</div>
</template>

<script>
  import SliderDots from './SliderDots'
  import SliderArrows from './SliderArrows'
  export default {
    components: {
      SliderDots,
      SliderArrows
    },
    data () {
      return {
        current: 0,
        autoPlayFlag: null
      }
    },
    props: {
      items: {
        type: Array,
        required: true
      },
      count: {
        type: Number,
        required: true,
        default: 3
      },
      dots: {
        type: Boolean,
        required: false,
        default: true
      },
      arrows: {
        type: Boolean,
        required: false,
        default: true
      },
      autoplay: {
        type: Boolean,
        required: false,
        default: true
      },
      delay: {
        type: Number,
        required: false,
        default: 2
      },
      speed: {
        type: Number,
        required: false,
        default: 1.5
      },
      pause: {
        type: Boolean,
        required: false,
        default: true
      }
    },
    methods: {
      turn (i) {
        let _i = this.current + i
        if (_i < 0) {
          (_i = _i + this.count)
        }
        if (_i >= this.count) {
          _i = _i - this.count
        }
        this.current = _i
      },
      goPlay () {
        if (this.autoplay) {
          this.autoPlayFlag = setInterval(() => {
            this.turn(1)
          }, this.delay * 1000)
        }
      },
      pausePlay () {
        clearInterval(this.autoPlayFlag)
      }
    },
    ready () {
      this.goPlay()
    }
  }
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
.slider {
  overflow: hidden;
  width: 100%;
  position: relative;
  top: -5px;
}
.slider > ul {
  height: 260px;
  overflow: hidden;
  position: relative;
  left: 0;
  transition: left 1s;
}
.slider .slider-item {
  display: inline-block;
  height: 260px;
}
.slider .slider-item > a > img {
  display: block;
  height: 260px;
  width: 100%;
}
.slider .slider-arrow {
  display: inline-block;
  color: #fff;
  font-size: 50px;
  position: absolute;
  top: 50%;
  margin-top: -50px;
  z-index: 100;
  padding: 20px;
  cursor: pointer;
  font-weight: bold;
}
.slider .slider-arrow:hover {
  background: rgba(0, 0, 0, 0.2);
}
.slider .slider-arrow.slider-arrow-right {
  right: 0;
}
.slider .slider-arrow.slider-arrow-left {
  left: 0;
}
.slider .slider-dots-wrap {
  z-index: 99;
  text-align: center;
  width: 100%;
  position: absolute;
  bottom: 0;
}
.slider .slider-dots-wrap .slider-dot {
  display: inline-block;
  width: 6px;
  height: 6px;
  border: 3px solid #ccc;
  margin: 6px;
  cursor: pointer;
  border-radius: 20px;
}
.slider .slider-dots-wrap .slider-dot:hover {
  border: 3px solid #868686;
}
.slider .slider-dots-wrap .slider-dot.slider-dot-selected {
  background: #ccc;
}
</style>