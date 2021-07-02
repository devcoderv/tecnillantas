<template>
  <section class="container">
    <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
      <article class="col-span-3 hidden lg:block">
        <div>
          <img src="/guia_llantas.png" alt="guia" class="w-full" />
          <div
            class="bg-gray-900 text-white h-10 flex items-center justify-center font-semibold text-xl"
          >
            Guia de llantas
          </div>
        </div>
      </article>
      <article class="col-span-9">
        <p class="text-2xl font-medium">Llantas</p>
        <p class="text-xl">Para un {{ car.name }}</p>
        <div class="border-gray-700 w-full h-px border-b mt-4"></div>
        <div class="container-llantas space-y-3 mt-4">
          <div
            v-for="(
              { _id, width, profile, rin, price, use, count, brandsLlantas },
              key
            ) in car.llantas"
            :key="_id"
            class="grid grid-cols-1 lg:grid-cols-3 gap-4 py-4 bg-gray-100"
          >
            <div class="px-4">
              <img src="/rueda.jpg" alt="" />
            </div>
            <div class="flex flex-col">
              <ul class="flex-1 place-content-around">
                <li>{{ width }}/{{ profile }} R{{ rin }}</li>
                <li class="text-lg font-medium">{{ brandsLlantas }}</li>
                <li>USO: {{ use }}</li>
                <li>DISPONIBILIDAD: {{ count }}</li>
              </ul>

              <nuxt-link
                active-class=" btn bg-red-600 hover:bg-red-500 text-white"
                exact-active-class="btn bg-red-600 hover:bg-red-500 text-white"
                class="text-center btn bg-red-600 hover:bg-red-500 text-white"
                :to="{ name: 'llantas-id', params: { id: _id } }"
                >Ver detalle</nuxt-link
              >
            </div>
            <div>
              <div class="flex price flex-col">
                <p class="font-bold border-gray-300 border-b pb-3">
                  Precio: {{ price }} COP
                </p>
                <p class="text-xs border-gray-300 border-b py-2">
                  Iva incluido | No Incluye Rin
                </p>
                <p class="border-gray-300 border-b py-2">Envio gratis</p>
                <div class="flex flex-wrap mt-7">
                  <div class="w-4/12">
                    <input-text
                      v-model="cantLlantas[key]"
                      type="number"
                    ></input-text>
                  </div>
                  <div class="w-8/12 flex justify-center items-center">
                    <p class="font-semibold">
                      Total: {{ cantLlantas[key] * price }} COP
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </article>
    </div>
  </section>
</template>

<script>
import InputText from '@/components/InputText.vue'
export default {
  components: {
    InputText,
  },
  async asyncData({ $http, $axios, params }) {
    const id = params.id
    const car = await $axios.$get(`/cars/${id}`)
    console.log(car)
    return { car }
  },
  data() {
    return {
      cantLlantas: [],
    }
  },
  computed: {
    // Canttotal() {
    //   for (let index = 0; index < this.car.llantas.length; index++) {
    //     this.cantLlantas.push(1)
    //   }
    //   return this.cantLlantas
    // },
  },

  mounted() {
    for (let index = 0; index < this.car.llantas.length; index++) {
      this.cantLlantas.push(1)
    }
  },
}
</script>
