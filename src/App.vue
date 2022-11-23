<template>
  <div id="app">
    <h1>Formulário Desafio</h1>
    <div class="conteudo">
      <!-- Para testar os campos sendo mudados em tempo real, é só tirar o v-if e o v-else no painel de resultado -->
      <!-- <form class="painel" v-if="!enviado"> -->
      <form class="painel">
        <div class="cabecalho">Formulário</div>

        <Rotulo nome="Nome completo:">
          <NomeSobrenome @enviarNS="preencherNomeSobrenome" />
        </Rotulo>

        <Rotulo nome="E-mail:">
          <input type="text" v-model="usuario.email" />
        </Rotulo>

        <Rotulo nome="Senha:">
          <input type="password" v-model="usuario.senha" />
        </Rotulo>

        <Rotulo nome="Armazenar dados?">
          <Escolha v-model="escolha" />
        </Rotulo>
        <hr />
        <button @click.prevent="enviar">Enviar</button>

        <!-- Exercicio 01 -->
        <!-- Criar uma formulário de registro -->
        <!-- Nome completo (Nome e Sobrenome) -->
        <!-- Email -->
        <!-- Senha -->
        <!-- Armazenar Dados? (Sim/Não) -->

        <!-- Exercicio 02 -->
        <!-- Só mostrar o fomulário de não tiver sido submetido -->
        <!-- Mostrar a área de Resultado apenas quando o formulário for submetido -->

        <!-- Exercicio 03 -->
        <!-- Crie um componente personalizado NomeCompleto -->
        <!-- Esse componente deve receber Nome e Sobrenome -->
      </form>
      <div class="painel">
        <!-- <div class="painel" v-else> -->

        <div class="cabecalho">Resultado</div>

        <Rotulo nome="Nome Completo: ">
          <span>{{ usuario.nome }} {{ usuario.sobrenome }}</span>
        </Rotulo>

        <Rotulo nome="E-mail:">
          <span>{{ usuario.email }}</span>
        </Rotulo>

        <Rotulo nome="Senha:">
          <span>{{ usuario.senha }}</span>
        </Rotulo>
        <Rotulo nome="Armazenhar Dados?">
          <span>{{ escolha ? "Sim" : "Não" }}</span>
        </Rotulo>
      </div>
    </div>
  </div>
</template>

<script>
import Rotulo from "./components/Rotulo.vue";
import Escolha from "./components/Escolha.vue";
import NomeSobrenome from "./components/NomeSobrenome.vue";

export default {
  name: "app",
  components: { Rotulo, Escolha, NomeSobrenome },
  data() {
    return {
      usuario: {
        nome: "",
        sobrenome: "",
        email: "",
        senha: "",
      },
      escolha: false,

      enviado: false,
    };
  },
  methods: {
    preencherNomeSobrenome(usuario) {
      this.usuario.nome = usuario.nome;
      this.usuario.sobrenome = usuario.sobrenome;
    },
    enviar() {
      this.enviado = true;
    },
  },
};
</script>

<style>
body {
  background-color: #ececec;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  display: flex;
  flex-direction: column;
}

.conteudo {
  display: flex;
}

.painel {
  flex: 1;
  background: #fff;
  margin: 0px 10px;
  padding: 20px;
  border: 1px solid #aaa;
  border-radius: 5px;
}

.painel .cabecalho {
  width: 100%;
  background-color: #ddd;
  padding: 10px 0px;
  border-radius: 5px;
  font-size: 1.4rem;
}

#app form button {
  float: right;
  margin: 10px 0px;
  padding: 10px 20px;
  font-size: 1.4rem;
  border-radius: 5px;
  color: #fff;
  background-color: #2196f3;
}

#app h1 {
  font-weight: 200;
  margin: 20px;
  padding: 0;
}

.mr-4 {
  margin-right: 40px;
}
</style>
