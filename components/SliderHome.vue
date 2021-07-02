<template>
  <div class="slider-container relative d-flex overflow-x-hidden">
    <div
      v-for="({ img }, i) in slider"
      :key="i"
      class="slider__item bg-center bg-no-repeat absolute bg-cover w-screen h-full slide transform transition-all flex items-center justify-center ease-in-out duration-1000 inset-0"
      :style="{
        'background-image': `url(${img})`,
        transform: `translateX(${(i - sliderPosition) * 100}%)`,
      }"
    >
      {{ (i - sliderPosition) * 100 }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      slider: [
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/LLANTAS-MODI.jpg',
          value: 0,
        },
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/Recurso-6.png',
          value: 1,
        },
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/Recurso-6.png',
          value: 1,
        },
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/Recurso-6.png',
          value: 1,
        },
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/Recurso-6.png',
          value: 1,
        },
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/Recurso-6.png',
          value: 1,
        },
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/Recurso-6.png',
          value: 1,
        },
      ],
      sliderPosition: 0,
    }
  },
  mounted() {
    this.init()
  },
  methods: {
    init() {
      setInterval(() => {
        // this.slider.map( (el, index) => {
        //   el. value
        // })

        this.sliderPosition === this.slider.length - 1
          ? (this.sliderPosition = 0)
          : this.sliderPosition++
        // setTimeout(() => {
        //   const a = this.slider.shift()
        //   this.slider.unshift()
        //   this.slider.push(a)
        // }, 2000)
      }, 3000)
    },
  },
}
</script>
<style>
.slider-container {
  height: 300px;
  @apply w-full;
}
@media (min-width: 1024px) {
  .slider-container {
    height: 600px;
  }
}
</style>
