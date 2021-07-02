<template>
  <section class="mt-6">
    <div
      class="services-container grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6"
    >
      <article v-for="({ img, text, map }, i) in cards" :key="i">
        <main class="relative flex items-center justify-center">
          <img :src="img" alt="" />
          <div class="absolute">
            <a
              class="bg-red-600 text-white py-2 px-6 rounded-md"
              :href="map"
              target="_seft"
              >{{ text }}</a
            >
          </div>
        </main>
      </article>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      cards: [
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/MONTALLANTAS-2-500x500.jpg',
          text: 'Montallantas',
          map: 'https://goo.gl/maps/Ute5AQ22NRAZHB7Z6',
        },

        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/ALINEACION-2-1000x1000.jpg',
          text: 'Alineacion',
          map: 'https://goo.gl/maps/Ute5AQ22NRAZHB7Z6',
        },
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/10/REC-RINES-2-500x500.jpg',
          text: 'Ret. Rines',
          map: 'https://goo.gl/maps/Ute5AQ22NRAZHB7Z6',
        },
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/10/BALANCEO-2-1000x1000.jpg',
          text: 'Balanceo',
          map: 'https://goo.gl/maps/Ute5AQ22NRAZHB7Z6',
        },
      ],
    }
  },
}
</script>
