<template>
  <div class="prose-sm prose sm:prose">
    <h2>Tabla de contentido</h2>
    <NuxtLink v-for="link in toc" :key="link.slug" :to="`#${link.id}`">
      <p v-if="link.depth === 2">
        <span class="mr-3 bullet">&#8226;</span>
        <span>{{ link.text }}</span>
      </p>
      <p v-else class="sublink">
        <span class="mr-2 bullet">&#8226;</span>
        <span>{{ link.text }}</span>
      </p>
    </NuxtLink>
  </div>
</template>

<script>
export default {
  props: ['toc'],
}
</script>
<style scoped>
.no-decoration {
  text-decoration: none !important;
}
.sublink {
  margin-left: 1.5em !important;
}
.bullet {
  color: var(--color-primary);
}
p {
  margin: 0;
}
a {
  margin: 0;
  text-decoration: none;
}
h2 {
  margin-bottom: 0;
}
</style>
