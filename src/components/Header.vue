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
   padding-right: calc(var(--section-gap) / 2);
 }

@media (min-width: 1024px) {
  header .header {
    display: flex;
    position: fixed;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>