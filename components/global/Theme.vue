<template>
  <div class="rounded-full" @click="toggleTheme">
    <svg
      v-if="isDark"
      focusable="false"
      width="1.2em"
      height="1.2em"
      viewBox="0 0 24 24"
    >
      <path
        d="M12 19.58c-1.6 0-3.11-.62-4.24-1.75A5.951 5.951 0 0 1 6 13.58c0-1.58.62-3.11 1.76-4.24L12 5.1m5.66 2.83L12 2.27L6.34 7.93c-3.12 3.12-3.12 8.19 0 11.31A7.98 7.98 0 0 0 12 21.58c2.05 0 4.1-.78 5.66-2.34c3.12-3.12 3.12-8.19 0-11.31z"
        fill="currentColor"
      ></path>
    </svg>
    <svg
      v-else
      focusable="false"
      width="1.2em"
      height="1.2em"
      viewBox="0 0 24 24"
    >
      <path
        d="M20.65 20.87L18.3 18.5L12 12.23L8.44 8.66L7 7.25L4.27 4.5L3 5.77l2.78 2.78a8.005 8.005 0 0 0 .56 10.69A7.98 7.98 0 0 0 12 21.58c1.79 0 3.57-.58 5.03-1.78l2.7 2.7L21 21.23l-.35-.36M12 19.59c-1.6 0-3.11-.62-4.24-1.76A5.945 5.945 0 0 1 6 13.59C6 12.27 6.43 11 7.21 10L12 14.77v4.82M12 5.1v4.58l7.25 7.26a7.99 7.99 0 0 0-1.6-9.01L12 2.27l-3.7 3.7l1.41 1.41L12 5.1z"
        fill="currentColor"
      ></path>
    </svg>
    {{ $colorMode.value }}
  </div>
</template>

<script>
export default {
  name: 'MdiInvertColors',
  data: () => ({
    isDark: false,
  }),
  mounted() {
    this.isDark = this.$colorMode.value !== 'light'
  },
  methods: {
    toggleTheme() {
      this.isDark = !this.isDark
      this.$colorMode.preference = this.isDark ? 'light' : 'dark'
    },
  },
}
</script>
