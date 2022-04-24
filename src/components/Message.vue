<template>
  <div class="message-container">
    <h2>{{ msg }}</h2>
  </div>
</template>

<script>
export default {
  name: 'Message',

  props: {
    msg: String,
  },
}
</script>

<style scoped>
.message-container {
  width: max-content;
  margin-right: auto;
  border: 1px solid black;
  background-color: rgba(0, 0, 0, 0.1);
  border-radius: 3px;
  padding: 5px;
}

h2 {
  color: green;
  font-size: 18px;
}
</style>
