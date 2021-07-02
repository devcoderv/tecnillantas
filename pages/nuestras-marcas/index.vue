<template>
  <section class="mt-6 container mx-auto">
    <div class="services-container grid grid-cols-2 md:grid-cols-3 gap-6">
      <div
        v-for="(img, key) in pictures"
        :key="key"
        class="flex justify-center items-center"
      >
        <img :src="img" alt="" />
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      pictures: [
        'https://tecnillantas.com.co/wp-content/uploads/2019/09/KT2.png',
        'https://tecnillantas.com.co/wp-content/uploads/2019/09/MI2.png',
        'https://tecnillantas.com.co/wp-content/uploads/2019/09/W2.png',
        'https://tecnillantas.com.co/wp-content/uploads/2019/09/R2.png',
        'https://tecnillantas.com.co/wp-content/uploads/2019/09/PI2.png',
        'https://tecnillantas.com.co/wp-content/uploads/2019/09/MAS2-1.png',
        'https://tecnillantas.com.co/wp-content/uploads/2019/09/GT2.png',
        'https://tecnillantas.com.co/wp-content/uploads/2019/09/image-3-2.png',
        'https://tecnillantas.com.co/wp-content/uploads/2019/09/image-3-1.png',
      ],
    }
  },
}
</script>
