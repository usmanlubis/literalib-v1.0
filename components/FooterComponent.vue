<template>
  <footer class="bg-light">
      <p class="text-center">
        &copy; {{ year }} LiteraLib. Made with ❤️ by <a href="https://github.com/usmanlubis" target="_blank">Usman Lubis</a>.
      </p>
  </footer>
</template>

<script>
  export default {
    data() {
      return {
        year: new Date().getFullYear(),
      }
    }
  }
</script>

