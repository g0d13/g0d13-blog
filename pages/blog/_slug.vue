<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()

    return {
      article,
    }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('es', options)
    },
  },
}
</script>

<template>
  <article class="container mx-auto max-w-screen-sm">
    <h1 class="text-5xl font-bold">{{ article.title }}</h1>
    <p class="mb-2">{{ article.description }}</p>
    <img
      :src="article.img"
      :alt="article.alt"
      class="w-full h-64 object-cover"
    />
    <p class="text-right mb-6">{{ formatDate(article.updatedAt) }}</p>
    <ul class="my-4">
      <li v-for="link of article.toc" :key="link.id" class="text-right">
        <NuxtLink
          :to="`#${link.id}`"
          :class="{
            'py-4': link.depth === 2,
            'mr-4 pb-4 bg-red': link.depth >= 3,
          }"
        >
          {{ link.text }}
        </NuxtLink>
      </li>
    </ul>
    <nuxt-content :document="article" />
  </article>
</template>

<style>
.nuxt-content > h1,
h2,
h3 {
  @apply font-bold mb-3;
}

.nuxt-content h1 {
  @apply text-3xl;
}
.nuxt-content h2 {
  @apply text-2xl;
}
.nuxt-content h3 {
  @apply text-xl;
}
.nuxt-content p {
  margin-bottom: 20px;
}

.icon.icon-link {
  background: url('~assets/svg/icon-hashtag.svg');
  display: inline-block;
  width: 20px;
  height: 20px;
  background-size: 20px 20px;
  fill: var(--color) !important;
}
.icon.icon-link > svg > path {
  /*target the image with css*/
  fill: var(--color);
}

.nuxt-content-highlight {
  @apply relative;
}
.nuxt-content-highlight .filename {
  @apply absolute right-0 text-gray-600 font-light z-10 mr-2 mt-1 text-sm;
}
</style>
