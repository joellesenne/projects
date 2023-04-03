<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      A concentrate of projects carried out on
      <br>
      <a href="https://github.com/joellesenne" target="_blank" rel="noopener">Github</a> for
      <a href="https://joellesenne.dev/" target="_blank" rel="noopener">Joellesenne</a>.
    </h3>
  </div>
</template>

<script>
import {defineComponent} from 'vue';

export default defineComponent({
  props: {
    msg: {
      type: String,
      required: true
    }
  },
})
</script>

<style scoped>
.greetings {
  width: 100%;
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings {
    position: fixed;
    top: 2.5rem;
    text-align: left;
  }
}
</style>