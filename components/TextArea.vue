<template>
  <!--
  This example requires Tailwind CSS v2.0+

  This example requires some changes to your config:

  ```
  // tailwind.config.js
  module.exports = {
    // ...
    plugins: [
      // ...
      require('@tailwindcss/forms'),
    ]
  }
  ```
-->
  <div>
    <label for="price" class="block text-sm font-medium text-gray-700">{{
      label
    }}</label>
    <div class="mt-1 relative rounded-md shadow-sm">
      <textarea
        v-model="value"
        class="focus:ring-red-500 focus:border-red-500 block w-full pl-7 pr-12 sm:text-sm border-gray-300 rounded-md transition-colors ease-in-out duration-700 resize-none h-44"
        :placeholder="placeholder"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    model: {
      type: String,
      default: '',
    },
    type: {
      type: String,
      default: 'text',
    },
    label: {
      type: String,
      default: '',
    },
    placeholder: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      item: '',
    }
  },
  computed: {
    value: {
      get() {
        return this.model
      },
      set(value) {
        this.$emit('input', value)
      },
    },
  },
}
</script>
