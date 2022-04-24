<template>
  <div id="nav">
    <router-link to="/">Home</router-link>
    <router-link to="/edit">Novo Contato</router-link>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
}
</script>

<style scoped>
* {
  padding: 0px;
  margin: 0px;
}

#nav {
  background-color: rgba(0, 0, 0, 0.5);
  border-bottom: 4px solid #111;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

#nav a {
  color: black;
  text-decoration: none;
  margin: 12px;
  transition: 0.5s;
  font-family: 'Lucida Sans', Verdana, sans-serif;
  font-weight: bold;
}

#nav a:hover {
  color: bisque;
}
</style>
