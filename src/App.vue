<template>
  <div>
    <Navbar />
    <router-view />
    <Card />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Card from './components/Card.vue'

export default {
  components: {
    Navbar,
  },
}
</script>

<style>
* {
  font-family: 'Lucida Sans', Verdana, sans-serif;
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}
</style>
