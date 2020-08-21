<template>
  <button>
    <slot />
  </button>
</template>

<script>
export default {}
</script>

<style>
.btn {
  @apply px-4 py-2 font-semibold rounded;
}

.btn-outlined {
  @apply bg-transparent border;
  &: hover {
    @apply border-transparent;
  }
}

.btn-disabled {
  @apply opacity-50 cursor-not-allowed;
}

.btn-blue {
  @apply text-blue-700 border-blue-500;
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
