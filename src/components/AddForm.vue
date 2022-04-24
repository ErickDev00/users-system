<template>
  <div>
    <Message :msg="msg" v-show="msg" />
    <div>
      <form id="main-form" @submit="createContact">
        <div class="input-container">
          <label for="Nome">Nome do Contato:</label>
          <input
            type="text"
            name="Nome"
            id="inputtext"
            v-model="nome"
            placeholder="Digite o nome"
          />
        </div>

        <div class="input-container">
          <label for="fone">Número do Contato:</label>
          <input
            type="tel"
            name="fone"
            id="fone"
            v-model="fone"
            placeholder="Digite o número ex:XXXXXXXXX"
            required
            pattern="[0-9]{9}"
          />
        </div>

        <div class="input-container">
          <label for="fone">Email:</label>
          <input
            type="email"
            name="mail"
            id="mail"
            v-model="mail"
            placeholder="Digite o Email"
            required
          />
        </div>

        <div>
          <input type="submit" class="submit-btn" value="Criar Contato" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Message from './Message.vue'
export default {
  components: { Message },
  name: 'AddForm',

  data() {
    return {
      nome: null,
      fone: null,
      mail: null,
      msg: null,
    }
  },

  methods: {
    async createContact(e) {
      e.preventDefault()

      //console.log('carro cadastrado com sucesso!')
      //coletando as informaçoes do formulário.

      const data = {
        nome: this.nome,
        fone: this.fone,
        mail: this.mail,
      }

      //console.log(data)
      //transformando dados de objetos para tipo texto.

      const dataJson = JSON.stringify(data)

      //enviando os dados convertidos para o db json.

      const req = await fetch('http://localhost:3004/contatos', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: dataJson,
      })

      const res = await req.json()

      console.log(res)

      //mensagem de cadastro
      this.msg = `Usuário ${this.nome} Cadastrado com Sucesso, Have a nice day!`

      //limpar a mensagem
      setTimeout(() => (this.msg = ''), 3000)

      //limpar campos.

      this.nome = ''
      this.fone = ''
      this.mail = ''
    },

    components: {
      Message,
    },
  },
}
</script>

<style scoped>
#main-form {
  max-width: 400px;
  margin: 0 auto;
}

.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
  margin-top: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: black;
  padding: 5px 10px;
  border-left: 4px solid red;
}

input {
  padding: 5px 10px;
  width: 300px;
}

.submit-btn {
  background-color: rgba(0, 0, 0, 0.5);
  color: black;
  font-weight: bold;
  border: none;
  border-radius: 10px;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.submit-btn:hover {
  background-color: rgba(0, 0, 0, 0.3);
}
</style>
