<template>
  <div>
    <section class="container grid grid-cols-12 mt-8">
      <div class="col-span-4">
        <img src="/llantas-prod.jpg" alt="" srcset="" />
      </div>
      <div class="col-span-6 p-4">
        <h1 class="font-bold text-4xl">{{ llanta.name }}</h1>
        <p class="font-medium text-xl my-2">
          {{ llanta.width }}/{{ llanta.profile }} R{{ llanta.rin }}
        </p>
        <p class="text-sm">Código: {{ llanta._id }}</p>
        <div class="mt-4 bg-gray-100 p-4">
          <div
            class="flex justify-between px-4 pb-2"
            v-for="({ text, value }, key) in details"
            :key="key"
          >
            <div class="flex-1">
              <p class="">{{ text }}</p>
            </div>

            <div class="text-left flex-1">
              <p class="font-semibold">{{ value }}</p>
            </div>
          </div>
        </div>
        <div class="my-6">
          <div class="flex justify-between px-4 pb-2">
            <div class="">
              <p class="uppercase text-xl">Precio ahora</p>
              <p class="font-semibold text-red-600 text-2xl">
                COP {{ llanta.price }}
                <span class="text-sm text-gray-600">c/u</span>
              </p>
              <p class="text-xs my-3">IVA INCLUIDO | NO INCLUYE RIN</p>
              <p class="text-sm">DISPONIBILIDAD: CONSULTE AQUÍ</p>
            </div>

            <div class="uppercase text-xl">
              <p class="">Precio Regular</p>
              <p class="text-2xl">
                <span class="line-through text-2xl"
                  >COP {{ llanta.price }}</span
                >

                <span class="text-sm text-gray-600 no-underline">c/u</span>
              </p>
            </div>
          </div>
        </div>
        <div class="border-b border-t border-gray-500 px-4 py-2">
          <p>ENVÍO GRATIS</p>
        </div>
        <div class="mt-4 px-4 grid grid-cols-12 gap-4">
          <div class="col-span-2">
            <input-text v-model="count" type="number"></input-text>
          </div>
          <div class="col-span-8 flex">
            <p class="font-bold text-3xl mr-4">${{ llanta.price * count }}</p>
            <button class="btn bg-red-600 text-white">Comprar</button>
          </div>
        </div>
      </div>
    </section>
    <section class="container mt-8">
      <div>
        <ul class="flex space-x-2">
          <li
            v-for="{ text, action } in options"
            :key="action"
            :class="[
              actions === action
                ? 'bg-gray-200 border-t-4 border-red-500 opacity-1'
                : 'bg-gray-400 opacity-50 text-gray-600',
              'p-3 w-40 text-center transition duration-500 ease-in-out font-medium cursor-pointer',
            ]"
            @click="actions = action"
          >
            {{ text }}
          </li>
        </ul>
      </div>
      <div class="bg-gray-200 p-8">
        <div
          v-show="actions === 'description'"
          v-html="llanta.description"
        ></div>
        <div v-show="actions === 'feature'" v-html="llanta.feature"></div>
        <div v-show="actions === 'benefits'" v-html="llanta.benefits"></div>
      </div>
    </section>
    <section class="container mt-8">
      <h2 class="font-medium uppercase text-3xl">TAMBIÉN TE PUEDE INTERESAR</h2>
      <div class="grid grid-cols-12 gap-8 pt-4">
        <article v-for="i in 3" :key="i" class="col-span-4">
          <header class="mx-auto relative">
            <img src="/more.jpg" alt="" srcset="" class="w-5/6 mx-auto" />
            <div class="bg-black text-white p-4 w-full">
              <p>{{ details[3].value }}</p>
              <p class="font-semibold text-xl">{{ llanta.name }}</p>
              <p>Uso: {{ llanta.use }}</p>
            </div>
          </header>
          <main class="bg-gray-200 p-4">
            <div class="flex mb-4">
              <div class="uppercase flex-1">
                <p class="">Precio ahora</p>
                <p class="font-bold text-red-600">
                  COP {{ llanta.price }}
                  <span class="text-sm text-gray-600">c/u</span>
                </p>
                <p class="text-xs my-3">IVA INCLUIDO | NO INCLUYE RIN</p>
              </div>
              <div class="uppercase flex-1">
                <p class="">Precio Regular</p>
                <p class="">
                  <span class="line-through">COP {{ llanta.price }}</span>

                  <span class="text-sm text-gray-600 no-underline">c/u</span>
                </p>
              </div>
            </div>
            <div class="text-center">
              <button class="btn bg-red-600 text-white">Ver detalle</button>
            </div>
          </main>
        </article>
      </div>
    </section>
  </div>
</template>

<script>
import InputText from '@/components/InputText.vue'
export default {
  components: { InputText },
  async asyncData({ $http, $axios, params }) {
    const id = params.id
    const llanta = await $axios.$get(`/llantas/${id}`)
    return { llanta }
  },
  data() {
    return {
      count: 1,
      actions: 'description',
      options: [
        { text: 'Description', action: 'description' },
        { text: 'Caracteristicas', action: 'feature' },
        { text: 'Beneficio', action: 'benefits' },
      ],
    }
  },
  computed: {
    details() {
      return [
        { text: 'Tipo de vehiculo', value: this.llanta.use },
        { text: 'Uso', value: this.llanta.use },
        { text: 'Diseño', value: this.llanta.name },
        {
          text: 'Medida',
          value: `${this.llanta.width}/${this.llanta.profile} R${this.llanta.rin}`,
        },
        { text: 'Indice de Velocidad (max)', value: '88' },
        { text: 'Velocidad Maxima', value: '3000' },
        { text: 'Índice de Carga', value: 88 },
        { text: 'Carga Máxima por Llanta', value: 88 },
        { text: 'Tecnología', value: 88 },
        { text: 'Marca', value: 88 },
      ]
    },
  },
}
</script>
