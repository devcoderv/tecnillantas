<template>
  <article>
    <header class="">
      <img class="mx-auto" :src="item.img" alt="" />
    </header>
    <main class="text-center">
      <h2 class="font-semibold text-3xl my-4">
        {{ item.title }}
        <br />
        <span class="text-red-600">{{ item.titleColor }}</span>
      </h2>
      <p class="text-gray-500 px-8">
        {{ item.content }}
      </p>
    </main>
  </article>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
      default: () => ({}),
    },
  },
}
</script>
