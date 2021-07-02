<template>
  <div>
    <header>
      <top-header text-left="BATERIAS Y DESPINCHES A DOMICILIOS"></top-header>
      <div class="container my-4 flex justify-center">
        <div class="bg-red-600 rounded-full p-8 w-52">
          <img
            class="w-full"
            src="https://tecnillantas.com.co/wp-content/uploads/2019/09/Recurso-8.png"
            alt=""
            srcset=""
          />
        </div>
      </div>
      <nav-bar :items="items"></nav-bar>
      <slider-home v-if="$route.name === 'index'"></slider-home>
      <div
        v-else-if="header"
        class="h-72 bg-cover bg-center bg-no-repeat flex justify-start items-center"
        :style="{
          'background-image': `url(${header.url})`,
        }"
      >
        <div class="container mx-auto text-white">
          <h1 class="text-5xl font-bold">{{ header.text }}</h1>
          <div class="w-1/12 of border-red-600 border-b-2 my-3"></div>
        </div>
      </div>
    </header>
    <main>
      <Nuxt />
    </main>
  </div>
</template>

<script>
import NavBar from '@/components/shared/NavBar.vue'
import TopHeader from '@/components/shared/TopHeader.vue'
import SliderHome from '@/components/SliderHome.vue'

export default {
  components: {
    NavBar,
    SliderHome,
    TopHeader,
  },
  data() {
    return {
      items: [
        { to: '/', text: 'Inicio' },
        {
          to: '/servicios',
          text: 'Servicios',
          url:
            'https://tecnillantas.com.co/wp-content/uploads/2019/10/motor.png',
        },
        {
          to: '/nuestras-marcas',
          text: 'Nuestras Marcas',
          url:
            'https://tecnillantas.com.co/wp-content/uploads/2019/10/yutrek-background-slider11.jpg',
        },
        {
          to: '/contactanos',
          text: 'Contactanos',
          url:
            'https://tecnillantas.com.co/wp-content/uploads/2019/10/images-3.jpg',
        },
      ],
    }
  },
  computed: {
    header() {
      const title = this.items.find((item) => item.to === this.$route.path)
      console.log(title)
      return title
    },
  },
  mounted() {},
}
</script>
