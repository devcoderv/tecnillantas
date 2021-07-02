<template>
  <section class="container">
    <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
      <article class="col-span-3 hidden lg:block">
        <div>
          <img src="guia_llantas.png" alt="guia" class="w-full" />
          <div
            class="bg-gray-900 text-white h-10 flex items-center justify-center font-semibold text-xl"
          >
            Guia de llantas
          </div>
        </div>
      </article>
      <article class="col-span-9">
        <p class="text-2xl font-medium">Llantas Medida: 165/70 R13</p>
        <p class="text-xl">
          Para un Changue FREEEDON CAB SENCILLA / PLATON 2020
        </p>
        <div class="border-gray-700 w-full h-px border-b mt-4"></div>
        <div class="container-llantas space-y-3 mt-4">
          <div class="grid grid-cols-1 lg:grid-cols-3 gap-4 py-4 bg-gray-100">
            <div class="px-4">
              <img src="/rueda.jpg" alt="" />
            </div>
            <div class="flex flex-col">
              <ul class="flex-1 place-content-around">
                <li>165/70 R13</li>
                <li class="text-lg font-medium">BF GOODRICH TOURING</li>
                <li>USO: Autopista (H/T)</li>
                <li>DISPONIBILIDAD: CONSULTE AQUÍ</li>
              </ul>

              <nuxt-link
                active-class=" btn bg-red-600 hover:bg-red-500 text-white"
                class="text-center"
                :to="{ name: 'llantas-id', params: { id: _id } }"
                >Ver detalle</nuxt-link
              >
            </div>
            <div>
              <div class="flex price">
                <p>Precio en oferta</p>
                <p>Precio</p>
              </div>
            </div>
          </div>
        </div>
      </article>
    </div>
  </section>
</template>

<script>
export default {}
</script>
