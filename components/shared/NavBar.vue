<template>
  <div class="navbar">
    <div class="navbar-content justify-center md:flex hidden">
      <nav class="main-menu">
        <li
          v-for="({ to, text }, key) in items"
          :key="key"
          class="main-menu__item"
        >
          <nuxt-link
            :to="to"
            class="main-menu__link font-medium text-gray-800"
            >{{ text }}</nuxt-link
          >
        </li>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: false,
      default: () => [],
    },
  },
}
</script>

<style scoped>
.navbar {
  @apply bg-gray-200 py-3;
}
.navbar-content {
  @apply md:container md:mx-auto;
}
.main-menu {
  @apply space-x-4;
}
.main-menu__item {
  @apply list-none inline-block;
}
</style>
