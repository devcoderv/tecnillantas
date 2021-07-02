<template>
  <div class="bg-black">
    <div
      class="flex container justify-between text-white px-8 py-3 italic font-medium"
    >
      <p>{{ textLeft }}</p>
      <p>SOLICITA TU ASISTENCIA INMEDIATA</p>
      <div class="text-red-600">llamanos escribenes whatsapp</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    textLeft: {
      type: String,
      requiret: true,
      default: 'Hola',
    },
  },
}
</script>
