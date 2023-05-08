<script setup>
import { ref } from 'vue'
const name = ref('')
const date = ref()
const mail = ref('')
const state = ref('')
const city = ref('')
const adress = ref('')
const hobbi = ref('')
const langP = ref('')
const biografia = ref('')
const senha = ref('')
const confirmaSenha = ref('')
const mostrar = ref(true)
const parametro = ref(false)
const SenhaE = ref(false)
const text = ref('As senhas estão diferentes.')

const usuario = ref({
  nome: name,
  email: mail,
  dm: date,
  estado: state,
  cidade: city,
  endereco: adress,
  hobbies: hobbi,
  lingProg: langP,
  bio: biografia,
  pass: senha
})

function falses() {
    parametro.value = false
    SenhaE.value = false
  }

function login() {
  if (name.value.length < 3 || biografia.value.length < 3 || langP.value.length < 1 || hobbi.value.length < 3  || mail.value.length < 3 || city.value.length < 3 || adress.value.length < 3) {
    parametro.value = true
    text.value = 'Preencha todos os parametros.'
  } else if (senha.value != confirmaSenha.value) {
    //alert("senha incorreta")
    text.value = 'As senhas estão diferentes'
    SenhaE.value = true
  }
  else {
    mostrar.value = !mostrar.value
    falses()
  }
}
</script>

<template>
  <div v-if="parametro || SenhaE" class="alert">
    <span class="closebtn" @click="falses">&times;</span>
    <strong>Erro!</strong> {{ text }}
  </div>

  <main class="container">
    <h2>Formulário Desenvolvimento-Web | Eduardo de Oliveira | 2info2 |</h2>
    <div v-if="mostrar">
      <form @submit.prevent="login">
        <div class="input-field">
          <input type="text" v-model="name" placeholder="Seu nome" minlength="3">
          <div class="underline"></div>
        </div>
        <div class="input-field">
          <input type="email" v-model="mail" placeholder="Seu email" minlength="3">
          <div class="underline"></div>
        </div>
        <div class="input-field">
          <input type="text" v-model="city" placeholder="cidade" minlength="3" />
          <div class="underline"></div>
        </div>
        <div class="input-field">
          <input type="text" v-model="adress" placeholder="Seu endereço" minlength="3" />
          <div class="underline"></div>
        </div>
        <div class="input-field">
          <input type="text" v-model="hobbi" placeholder="Seus hobbies" minlength="3" />
          <div class="underline"></div>
        </div>
        <div class="input-field">
          <input type="text" v-model="langP" placeholder=" Suas linguagens de prog" minlength="3" />
          <div class="underline"></div>
        </div>
        <div class="input-field">
          <input type="text" v-model="biografia" placeholder="Sua biografia" minlength="3" />
          <div class="underline"></div>
        </div>
        <div class="input-field">
          <label>Data de nascimento:</label>
          <input v-model="date" type="date" placeholder="Data de nascimento">
          <div class="underline"></div>
        </div>
        <div class="input-field">
          <label>Selecione seu estado:</label>
          <select v-model="state">
            <option value="AC">Acre</option>
            <option value="AL">Alagoas</option>
            <option value="AP">Amapa</option>
            <option value="AM">Amazonas</option>
            <option value="BA">Bahia</option>
            <option value="CE">Ceara</option>
            <option value="DF">Distrito Federal</option>
            <option value="ES">Espirito Santo</option>
            <option value="GO">Goiania</option>
            <option value="AC">Acre</option>
            <option value="MA">Maranhão</option>
            <option value="MT">Mato Grosso</option>
            <option value="MS">Mato Groso do Sul</option>
            <option value="MG">Minas Gerais</option>
            <option value="PA">Para</option>
            <option value="PB">Paraiba</option>
            <option value="PE">Pernanbuco</option>
            <option value="PI">Piauí</option>
            <option value="PR">Paraná</option>
            <option value="RJ">Rio de Janeiro</option>
            <option value="RN">Rio Grande do Norte</option>
            <option value="RS">Rio Grande do Sul</option>
            <option value="RO">Rondonia</option>
            <option value="RR">Roraima</option>
            <option value="SC">Santa Catarina</option>
            <option value="SP">São Paulo</option>
            <option value="SE">Sergipe</option>
            <option value="TO">Tocantins</option>
          </select>
          <div class="underline"></div>
        </div>
        <div class="input-field">
          <input type="password" v-model="senha" placeholder="Sua senha" maxlength="20" />
          <div class="underline"></div>
        </div>
        <div class="input-field">
          <input type="password" v-model="confirmaSenha" placeholder="Confirme sua senha" maxlength="20" />
          <div class="underline"></div>
        </div>
        <input @click="login" class="btn-info" type="submit" value="Cadastrar info">
      </form>
    </div>
    <div v-else>
      <div class="input-field">
        <label>Seu nome e {{ usuario.nome }}</label>
        <div class="underline"></div>
      </div>
      <div class="input-field">
        <label>Seus hobbies sao: {{ usuario.hobbies }}</label>
        <div class="underline"></div>
      </div>
      <div class="input-field">
        <label>Suas linagens sao: {{ usuario.lingProg }}</label>
        <div class="underline"></div>
      </div>
      <div class="input-field">
        <label>Seu endereco e {{ usuario.endereco }}</label>
        <div class="underline"></div>
      </div>
      <div class="input-field">
        <label>Sua cidade e {{ usuario.cidade }}</label>
        <div class="underline"></div>
      </div>
      <div class="input-field">
        <label>Sua biografia e: {{ usuario.bio }}</label>
        <div class="underline"></div>
      </div>
      <div class="input-field">
        <label>Sua data de nascimento e: {{ usuario.dm }}</label>
        <div class="underline"></div>
      </div>
      <div class="input-field">
        <label>Seu email e {{ usuario.email }}</label>
        <div class="underline"></div>
      </div>
      <div class="input-field">
        <label>Seu estado e {{ usuario.estado }}</label>
        <div class="underline"></div>
      </div>
      <input @click="login" class="btn-info" type="submit" value="Editar info">
    </div>

  </main>
</template>

<style scoped>
main.container {
  background: rgba(192, 192, 192, 0.815);
  min-width: 320px;
  min-height: 40vh;
  padding: 2rem;
  box-shadow: 5px 5px 15px rgba(192, 192, 192, 0.815);
  border-radius: 8px;
}

main h2 {
  font-weight: 600;
  margin-bottom: 2rem;
  position: relative;
}

form {
  display: flex;
  flex-direction: column;
}

.input-field {
  margin: 10px;
  padding: 10px;
  background-color: transparent;
  position: relative;
}

form .input-field:first-child {
  margin-bottom: 1.5rem;
}

.input-field .underline::before {
  content: '';
  position: absolute;
  height: 1px;
  width: 100%;
  bottom: -5px;
  left: 0;
  background: rgba(192, 192, 192, 0.815);
}

.input-field .underline::after {
  content: '';
  position: absolute;
  height: 1px;
  width: 100%;
  bottom: -5px;
  left: 0;
  background-color: rgba(192, 192, 192, 0.815);
  transform: scaleX(0);
  transition: all .3s ease-in-out;
  transform-origin: left;
}

.input-field input:focus~.underline::after {
  transform: scaleX(1);
}

.input-field input {
  background-color: transparent;
  outline: none;
  font-size: 0.9rem;
  color: rgba(0, 0, 0, 0.7);
  width: 100%;
}

select {
  margin-top: 10px;
  border-radius: 5px;
  background-color: rgba(192, 192, 192, 0.815);
  padding-left: 10px;
  margin-left: 10px;
  width: auto;
}

form input[type="date"] {
  margin-top: 10px;
  border-radius: 5px;
  background-color: rgba(192, 192, 192, 0.815);
  padding-left: 10px;
  margin-left: 10px;
  width: auto;
}

.input-field input::placeholder {
  color: rgba(0, 0, 0, 0.5);
}

.btn-info {
  margin-top: 2rem;
  padding: 0.4rem;
  width: 100%;
  background-color: rgba(192, 192, 192, 0.815);
  ;
  cursor: pointer;
  color: white;
  font-size: 0.9rem;
  font-weight: 300;
  border-radius: 4px;
  transition: all 0.3s ease;
}

.btn-info :hover {
  transition: 5ms;
  letter-spacing: 0.5px;
  background: linear-gradient(to right, #5f6675, #537075);
}

.closebtn {
  margin-top: 3px;
  margin-left: 15px;
  color: white;
  font-weight: bold;
  float: right;
  font-size: 22px;
  line-height: 20px;
  cursor: pointer;
  transition: 0.3s;
}

.closebtn:hover {
  color: black;
}

.alert {
  padding: 20px;
  background-color: #f44336;
  color: white;
  width: 90%;
  margin-bottom: 10px;
  border-radius: 10px;
  text-align: center;
}
</style>