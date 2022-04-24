<template>
  <div>
    <div class="contact-card">
      <h3>teste</h3>
      <h4>Contato: <span class="info">000000000</span></h4>
      <h4>Email: <span class="info">teste@teste.com</span></h4>
      <button id="action-btn">Editar</button>
      <button id="action-btn">Excluir</button>
      {{ contato }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  data() {
    return {
      id: this.$route.params.id,
      contato: [],
    }
  },

  mounted() {
    fetch('http://localhost3004/contatos')
      .then((resp) => resp.json())
      .then((data) => (this.contato = data))
  },
}
</script>

<style scoped>
h3 {
  font-size: 20px;
}

h3,
h4 {
  padding: 5px;
}

#name-contact {
  font-size: 17px;
}

.contact-card {
  display: flex;
  flex-direction: column;
  width: max-content;
  margin-top: 7%;
  margin-left: 20%;
  border: 1px solid black;
}

#action-btn {
  width: 60px;
  cursor: pointer;
}
</style>
