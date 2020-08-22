<template>
  <div class="container mx-auto">
    <article
      class="prose-sm prose md:mx-10 lg:mx-20 xl:mx-40 sm:prose max-w-none"
    >
      <h1>{{ page.title }}</h1>
      <nuxt-content :document="page"></nuxt-content>
    </article>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const page = await $content('hello').fetch()
    return {
      page,
    }
  },
}
</script>

<style>
.prose * {
  color: var(--color) !important;
}

.prose code {
  font-weight: 600;
  font-size: 0.875em;
}

.max-w-none {
  max-width: none;
}
</style>
