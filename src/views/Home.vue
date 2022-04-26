<template>
  <div class="main-container">
    <h1>Usuários Cadastrados</h1>
    <Card />
  </div>
</template>

<script>
import Card from '../components/Card.vue'

export default {
  name: 'Home',
  components: {
    Card,
  },
}
</script>
