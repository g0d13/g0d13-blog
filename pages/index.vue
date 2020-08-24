<template>
  <div class="mx-auto max-w-screen-sm">
    <h1 class="text-4xl font-bold">Blog</h1>
    <ul class="mt-3">
      <li v-for="article in articles" :key="article.slug">
        <NuxtLink
          :to="{ name: 'blog-slug', params: { slug: article.slug } }"
          class="flex my-8"
        >
          <img :src="article.img" alt="Una imagen" class="h-32 w-32" />
          <div class="pl-5 flex flex-col">
            <h2 class="font-bold text-xl">{{ article.title }}</h2>
            <p class="italic text-sm">{{ article.author.name }}</p>
            <p class="text-justify">{{ article.description }}</p>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content('articles', params.slug)
      .only(['title', 'description', 'img', 'slug', 'author', 'createdAt'])
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      articles,
    }
  },
}
</script>
