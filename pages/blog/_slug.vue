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
    <toc :toc="article.toc" />
    <nuxt-content :document="article" />
  </article>
</template>

<style>
/* text color */
.prose > h1,
h2,
h3,
p,
a {
  color: var(--color) !important;
}
.icon.icon-link {
  background: var(--background);
  display: inline-block;
  margin-left: -20px;
  width: 20px;
  height: 20px;
  background-size: 20px 20px;
}
.prose h3 > a,
h2 > a {
  visibility: hidden;
}

.prose h2:hover > a,
h3:hover > a {
  visibility: visible;
}

.prose > h1:hover > a,
.prose > h2:hover > a,
.prose > h3:hover > a,
.prose h4:hover > a,
.prose dt.hdlist1:hover > a.anchor {
  visibility: visible !important;
}
.nuxt-content-highlight {
  @apply relative;
}
.nuxt-content-highlight .filename {
  @apply absolute right-0 text-gray-600 font-light z-10 mr-2 mt-1 text-sm;
}
</style>
