<template>
  <div class="">
    <section
      class="px-4 mt-4 transform md:-translate-y-16 md:-mt-3 container flex justify-center"
    >
      <div class="lg:w-5/6 w-full">
        <ul
          class="w-full text-gray-50 flex cursor-pointer flex-col md:flex-row"
        >
          <li
            class="py-2 px-6 transition-all ease-in-out duration-700 bg-black"
            :class="[tab === 0 ? ' text-red-500' : ' text-white bg-opacity-75']"
            @click="tab = 0"
          >
            <span class="block text-2xl font-medium">Buscar</span>
            <span class="text-lg"> Llantas por vehiculo </span>
          </li>
          <li
            class="py-2 px-6 transition-all ease-in-out duration-700 bg-black"
            :class="[
              tab === 1 ? '  text-red-500' : ' text-white bg-opacity-75 ',
            ]"
            @click="tab = 1"
          >
            <span class="block text-2xl font-medium">Buscar</span>
            <span class="text-lg"> Llantas por medida </span>
          </li>
        </ul>
        <div class="bg-black shadow-2xl shadow-outline">
          <div v-if="tab === 0" class="p-4 grid md:grid-cols-3 gap-4 w-full">
            <select ref="brands" class="p-2 select" @change="changeBrand">
              <option value="-1">Seleccionar marca</option>
              <option
                v-for="({ _id, name }, key) in brands"
                :key="_id"
                :value="key"
                :meta-id="_id"
              >
                {{ name }}
              </option>
            </select>
            <select class="p-2 select" @click="changeYear">
              <option value="-1">Seleccionar modelo (año)</option>
              <option v-for="(year, key) in years" :key="key" :value="year">
                {{ year }}
              </option>
            </select>
            <select class="p-2 select" @click="loadCar">
              <option value="-1">Seleccionar linea</option>
              <option
                v-for="({ _id, name }, key) in cars"
                :key="_id"
                :value="key"
                :meta-id="_id"
              >
                {{ name }}
              </option>
            </select>
          </div>
          <div v-else class="p-4 md:grid grid-cols-3 gap-4">
            <select class="p-2 select" @change="changeWidth">
              <option value="-1">Seleccionar ancho</option>
              <option v-for="rin in llantas" :key="rin" :value="rin">
                {{ rin }}
              </option>
            </select>
            <select class="p-2 select" @change="changeProfile">
              <option value="-1">Seleccionar perfil</option>
              <option
                v-for="profile in profiles"
                :key="profile"
                :value="profile"
              >
                {{ profile }}
              </option>
            </select>
            <select class="p-2 select" @change="loadllantas">
              <option value="-1">Seleccionar</option>
              <option v-for="({ rin }, key) in rins" :key="key" :value="rin">
                {{ rin }}
              </option>
            </select>
          </div>
        </div>
      </div>
    </section>
    <section class="">
      <h2 class="text-center container">Nuestras marcas</h2>
    </section>
    <section class="bg-gray-100 py-4">
      <div class="container mx-auto">
        <div class="flex flex-col items-center mb-8">
          <h2 class="uppercase text-3xl font-bold">¿Como lo Hago?</h2>
          <div class="w-1/12 of border-red-600 border-b-2 my-3"></div>
          <p>Sigue estos sencillos 3 pasos</p>
        </div>
        <div class="grid md:grid-cols-3 gap-6">
          <card-info
            v-for="(item, i) in cardInfo"
            :key="i"
            :item="item"
          ></card-info>
        </div>
      </div>
    </section>
    <section class="bg-gray-100 py-4">
      <div class="flex flex-col items-center mb-8">
        <h2 class="uppercase text-3xl font-bold">Productos & servcios</h2>
        <div class="w-1/12 of border-red-600 border-b-2 my-3"></div>
        <p>
          Tu auto en las manos expertas con una completa gama de servicios &
          productos especiales para ti.
        </p>
      </div>
    </section>
  </div>
</template>

<script>
import CardInfo from '@/components/CardInfo.vue'
export default {
  components: { CardInfo },
  props: {
    CardInfo,
  },

  async asyncData({ $http, $axios }) {
    const brands = await $axios.$get('/brands')
    const rinsAxios = await $axios.$get('/llantas')
    const llantas = []

    // const llantas = this.reduceArry(rinsAxios, 'width')
    const listRin = rinsAxios.map((el) => el.width)
    listRin.forEach((element) => {
      const resp = llantas.includes(element)
      !resp && llantas.push(element)
    })
    return { brands, llantas }
  },
  data() {
    return {
      tab: 0,
      // brands: [
      //   'ALFA ROMEO',
      //   'APRILLA',
      //   'AUDI',
      //   'BAIC',
      //   'BMW',
      //   'BRILLIANCE',
      //   'BYD',
      //   'CHANA',
      //   'CHANGAN',
      //   'CHANGHE',
      //   'CHANGUE',
      //   'CHERY',
      //   'CHEVROLET',
      //   'CHRYSLER',
      //   'CITROEN',
      //   'DAEWOO',
      //   'DAIHATSU',
      //   'DFSK',
      //   'DODGE',
      //   'DONG FENG ',
      //   'DUCATI',
      //   'FAW',
      //   'FERRARI',
      //   'FIAT',
      //   'FORD',
      //   'FOTON',
      //   'GEELY',
      //   'GREAT WALL',
      //   'HAFEI',
      //   'HAIMA',
      //   'HODAN',
      //   'HONDA',
      //   'HYUNDAI',
      //   'IVECO',
      //   'JAC',
      //   'JAGUAR',
      //   'JEEP',
      //   'JMC',
      //   'KENBO',
      //   'KIA',
      //   'LADA',
      //   'LAND ROVER',
      //   'LEXUS',
      //   'LIFAN',
      //   'MAHINDRA',
      //   'MASERATI',
      //   'MAZDA',
      //   'MERCEDES BENZ',
      //   'MG',
      //   'MINI',
      //   'MITSUBISHI',
      //   'NISSAN',
      //   'PEUGEOT',
      //   'PORSCHE',
      //   'RAM',
      //   'RENAULT',
      //   'ROVER',
      //   'SEAT',
      //   'SHINERAY',
      //   'SKODA',
      //   'SSANGYONG',
      //   'SUBARU',
      //   'SUZUKI',
      //   'TOYOTA',
      //   'VOLKSWAGEN',
      //   'VOLVO',
      //   'ZNA',
      //   'ZOTYE',
      // ],
      cardInfo: [
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/BUBUS-removebg-preview.png',
          title: 'BUSCA TU LLANTA',
          titleColor: 'A TU MEDIDA',
          content:
            'En nuestro buscador encontrarás siempre dos opciones para encontrar tus llantas perfectas, por medida o por vehiculo, con ello nos aseguramos a que siempre encuentres las mejores y las más específicas opciones para tu carro.',
        },
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/ENVV-removebg-preview.png',
          title: 'TU ENVÍO LOCAL',
          titleColor: 'GRATIS',
          content:
            'En Tecnillantas lo importante eres tú, elige tus llantas y nosotros las enviaremos gratis en Bogotá y Sopó al lugar que nos indiques, recuerda revisar nuestros  tiempos de envío.',
        },
        {
          img:
            'https://tecnillantas.com.co/wp-content/uploads/2019/09/SERVIIII.png',
          title: 'TECNICENTROS',
          titleColor: 'A TU MEDIDA',
          content:
            'Puedes recoger tus llantas en nuestros Tecnicentros y recibir el montaje de las mismas en cualquiera de nuestros 13 puntos propios.',
        },
      ],
      brands: [],
      years: [],
      cars: [],
      profiles: [],
      rins: [],
      width: [],
      profile: '',
      brandID: '',
      yearID: '',
    }
  },
  methods: {
    async changeBrand(event) {
      try {
        const index = event.target.value
        const brand = this.brands[index]
        if (index > -1) {
          this.brandID = brand._id
          const itemsyears = await this.$axios.$get(
            `/cars/brand/${this.brandID}`
          )
          const years = itemsyears.map((el) => el.year)
          const newYear = []
          years.forEach((element) => {
            const resp = newYear.includes(element)
            !resp && newYear.push(element)
            console.log(resp)
            console.log(newYear)
          })
          this.years = newYear

          console.log(this.years)
        }
      } catch (error) {
        console.log(error)
      }
    },
    async changeWidth(event) {
      try {
        this.width = event.target.value
        if (this.width > -1) {
          const llantas = await this.$axios.$get(
            `/llantas/?width=${this.width}`
          )
          this.profiles = this.reduceArry(llantas, 'profile')
        }
      } catch (error) {
        console.log(error)
      }
    },
    async changeProfile(event) {
      try {
        this.profile = event.target.value
        if (this.profile > -1) {
          const llantas = await this.$axios.$get(
            `/llantas/?width=${this.width}&profile=${this.profile}`
          )
          this.rins = llantas.map((el) => ({ rin: el.rin, id: el._id }))
        }
      } catch (error) {
        console.log(error)
      }
    },
    async changeYear(event) {
      try {
        this.yearID = event.target.value
        if (this.yearID > -1) {
          this.cars = await this.$axios.$get(
            `/cars/brand/${this.brandID}/year/${this.yearID}`
          )
          console.log('cars', this.cars)
        }
      } catch (error) {
        console.log(event)
      }
    },
    loadllantas(event) {
      try {
        const index = event.target.value
        if (index > -1) {
          const query = { width: this.width, profile: this.profile, rin: index }
          console.log('query', query)
          this.$router.push({
            name: 'llantas-medida',
            query,
          })
        }
      } catch (error) {}
    },
    loadCar(event) {
      try {
        const index = event.target.value
        if (index > -1) {
          const car = this.cars[index]
          console.log(car)
          this.$router.push({
            name: 'llantas-vehiculo-id',
            params: { id: car._id },
          })
        }
      } catch (error) {}
    },
    reduceArry(arrMap, prop) {
      const arr = arrMap.map((el) => el[prop])
      const arrResp = []
      arr.forEach((element) => {
        const resp = arrResp.includes(element)
        !resp && arrResp.push(element)
      })
      return arrResp
    },
  },
  // async fetch(context) {
  //   console.log(context)
  //   this.brands = await await context.$axios.$get('/brands')
  //   console.log(this.brands)
  // },
  // fetchOnServer: false,
}
</script>

<style>
/* .container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
} */
</style>
