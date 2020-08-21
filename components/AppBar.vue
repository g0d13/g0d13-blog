<template>
  <nav class="flex flex-row justify-end gap-6">
    <ul>
      Blog
    </ul>
    <ul>
      Recursos
    </ul>
    <ul>
      <a href="#" class="btn btn-outlined btn-blue">
        Acerca de
      </a>
    </ul>
  </nav>
</template>

<script>
export default {}
</script>

<style>
.btn {
  @apply px-4 py-2 font-semibold rounded;
}

.btn-outlined {
  @apply bg-transparent border border-blue-500;
  &: hover {
    @apply border-transparent;
  }
}

.btn-blue {
  @apply text-blue-700;
  &:hover {
    @apply bg-blue-500 text-white;
  }
}

@variants focus, hover {
  .rotate-0 {
    transform: rotate(0 deg);
  }
  .rotate-90 {
    transform: rotate(90 deg);
  }
}
</style>
