<template>
  <div id="contact-card">
    <Message :msg="msg" v-show="msg" />
    <div>
      <div id="user-heading">
        <div id="user-id">#:</div>
        <div>Nome:</div>
        <div>Contato:</div>
        <div>Email:</div>
        <div>Ações</div>
      </div>
    </div>

    <div id="user-rows">
      <div class="user-row" v-for="contato in contatos" :key="contato.id">
        <div class="user-number">{{ contato.id }}</div>
        <div>{{ contato.nome }}</div>
        <div>{{ contato.fone }}</div>
        <div>{{ contato.mail }}</div>

        <div>
          <button class="delete-btn" @click="deletarContato(contato.id)">
            Excluir Usuário
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Message from './Message.vue'
export default {
  name: 'Card',

  data() {
    return {
      contatos: null,
      contatos_id: null,
      msg: null,
    }
  },

  components: {
    Message,
  },

  //carregar os usuários

  methods: {
    async getContatos() {
      const req = await fetch('http://localhost:3004/contatos')

      const data = await req.json()

      this.contatos = data
    },

    async deletarContato(id) {
      const req = await fetch(`http://localhost:3004/contatos/${id}`, {
        method: 'DELETE',
      })

      const data = await req.json()

      //mensagem de cadastro
      this.msg = `Usuário removido com Sucesso, Have a nice day!`

      //limpar a mensagem
      setTimeout(() => (this.msg = ''), 3000)

      this.getContatos()
    },
  },

  mounted() {
    this.getContatos()
  },
}
</script>

<style scoped>
#contact-card {
  max-width: 1200px;
  margin: 0 auto;
  padding-top: 30px;
}

#user-heading,
#user-rows,
.user-row {
  display: flex;
  flex-wrap: wrap;
}

#user-heading {
  font-weight: bold;
  padding: 12px;
  border-bottom: 3px solid red;
}

#user-heading div,
.user-row div {
  width: 19%;
}

.user-row {
  width: 100%;
  padding: 12px;
  border-bottom: 1px solid black;
}

select {
  padding: 10px 6px;
  margin-right: 12px;
}

.delete-btn {
  background-color: gray;
  color: white;
  font-weight: bold;
  padding: 10px;
  font-size: 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: 0.5s;
}

.delete-btn:hover {
  background-color: red;
}
</style>
