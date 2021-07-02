<template>
  <section class="container mx-auto mt-8">
    <div></div>
    <div class="lg:px-48">
      <h2 class="text-center text-red-600 text-3xl font-bold mb-4">
        CONTÁCTENOS
      </h2>
      <p class="text-center">
        Para
        <span class="text-red-600 font-medium"
          >TECNILLANTAS ER lo más importante son sus clientes;</span
        >
        este espacio fue diseñado para su servicio: Queremos conocerte *
      </p>
      <form class="mt-8 flex flex-wrap" @submit.prevent="">
        <div class="w-full md:w-1/2 px-4 mb-4">
          <input-text v-model="name" label="Nombre" type="text"></input-text>
        </div>
        <div class="w-full md:w-1/2 px-4 mb-4">
          <input-text
            v-model="lastname"
            label="Apellido"
            type="text"
          ></input-text>
        </div>
        <div class="w-full md:w-2/3 px-4 mb-4">
          <input-select
            v-model="help"
            placeholder="Seleccionar"
            label="¿Qué podemos ayudarte el día de hoy?"
          ></input-select>
        </div>
        <div class="w-full md:w-1/2 px-4 mb-4">
          <input-text v-model="phone" label="Telefono" type="tel"></input-text>
        </div>
        <div class="w-full md:w-1/2 px-4 mb-4">
          <input-text
            v-model="email"
            label="Correo electronico"
            type="email"
          ></input-text>
        </div>
        <div class="w-full px-4 mb-4">
          <text-area label="Mensaje"></text-area>
        </div>
        <div class="w-full px-4 mb-4 flex justify-end">
          <input class="btn text-white" type="submit" value="Enviar" />
        </div>
      </form>
    </div>
  </section>
</template>

<script>
import InputText from '@/components/InputText.vue'
import TextArea from '~/components/TextArea.vue'
import InputSelect from '~/components/InputSelect.vue'
export default {
  components: { InputText, TextArea, InputSelect },

  data() {
    return {
      name: '',
      lastname: '',
      phone: '',
      email: '',
      help: '',
    }
  },
  methods: {
    hande() {
      console.log('change')
    },
  },
}
</script>
<style>
/* .btn {
  @apply py-2 px-6 rounded-md cursor-pointer border
    focus:ring-red-500 focus:border-red-500 text-white;
} */
</style>
