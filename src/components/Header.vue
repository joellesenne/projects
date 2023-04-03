<template>
  <header class="header">
    <HelloWorld msg="My projects" />
  </header>
</template>
<script>
import HelloWorld from "@/components/HelloWorld.vue";
export default {
  name: 'Header',
  components: { HelloWorld }
}
</script>

<style scoped>
.header {
  line-height: 1.5;
   display: flex;
   place-items: center;
 }

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>