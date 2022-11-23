<template>
  <!-- Esse foi um jeito que eu arrumei de renderizar o nome e o sobrenome( usando o input),
 sei que não está certo assim mais foi o mais proximo que consegui chegar -->
  <div @input="$emit('enviarNS', usuario)">
    <Rotulo nome="Nome">
      <input type="text" v-model="usuario.nome" />
    </Rotulo>

    <Rotulo nome="Sobrenome">
      <input type="text" v-model="usuario.sobrenome" />
    </Rotulo>
  </div>
</template>

<script>
import Rotulo from "./Rotulo.vue";
export default {
  props: ["nome", "sobrenome"],
  components: { Rotulo },

  data() {
    return {
      usuario: {
        nome: "",
        sobrenome: "",
      },
    };
  },
};
</script>

<style>
</style>