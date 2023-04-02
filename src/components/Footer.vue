<template>
  <footer class="footer">
    <p>&copy; 2019-{{ currentYear }} - All rights reserved - <a href="https://joellesenne.dev/" target="_blank" rel="noopener">Joellesenne</a></p>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data() {
    return {
      currentYear: new Date().getFullYear()
    }
  }
}
</script>

<style scoped>
.footer {
  margin: 1rem;
}
</style>
