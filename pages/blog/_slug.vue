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
  <article class="container mx-auto prose-sm prose sm:prose">
    <h1 class="text-5xl font-bold">{{ article.title }}</h1>
    <p class="mb-2">{{ article.description }}</p>
    <!-- Imagen -->
    <img
      :src="article.img"
      :alt="article.alt"
      class="object-cover w-full h-64 mb-0"
    />

    <p class="mt-0 text-right">{{ formatDate(article.updatedAt) }}</p>

    <ul class="my-4">
      <div v-if="article.toc !== 0">
        <h2>Tabla de contenidos</h2>
        <li v-for="link of article.toc" :key="link.id">
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
      </div>
    </ul>
    <nuxt-content :document="article" />
  </article>
</template>

<style>
/* .icon.icon-link {
  background: url('~assets/svg/icon-hashtag.svg');
  display: inline-block;
  width: 20px;
  height: 20px;
  background-size: 20px 20px;
  fill: var(--color) !important;
}
.icon.icon-link > svg > path {
  /*target the image with css
  fill: var(--color);
} */

.nuxt-content-highlight {
  @apply relative;
}
.nuxt-content-highlight .filename {
  @apply absolute right-0 text-gray-600 font-light z-10 mr-2 mt-1 text-sm;
}

.prose > h1,
h2,
h3,
p,
a {
  color: var(--color) !important;
}
</style>
