<template>
  <div>
    <h1 id="titulo">Cadastre-se</h1>
    <label for="formdoador">
      <input
        onclick="formdoador()"
        id="formdoador"
        type="radio"
        name="cadastro"
        value="Represento Doador"
      />
      Represento Doador</label
    >
    <form id="formularioD">
      <div class="col-md-6">
        <label for="nome-doador" class="form-label"> Nome </label>
        <input
          type="text"
          class="form-control"
          v-model="form.nome"
          id="nome-doador"
          required
        />
      </div>
      <div class="col-md-6">
        <label for="email-doador" class="form-label"> Email </label>
        <input
          type="text"
          class="form-control"
          v-model="form.email"
          id="email-doador"
          required
        />
      </div>
      <div class="col-md-5">
        <label for="senha-doador" class="form-label"> Senha </label>
        <input
          type="password"
          class="form-control"
          v-model="form.senha"
          id="senha-doador"
          required
        />
      </div>
      <button v-on:click="cadastrar" class="botao btn-primary">Concluído</button>
      <b-button v-on:click="deletar">deletar</b-button>
      <h1 id="deletar"></h1>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        nome: '',
        email: '',
        senha: '',
      },
      show: true,
    }
  },

  methods: {
    cadastrar({ $axios }) {
      this.$axios.post('/doador', {
        nome: this.form.nome,
        email: this.form.email,
        senha: this.form.senha,
      })
    },

    deletar({ $axios }){
        this.$axios.delete('/deletaDoador/3');
        const result = document.getElementById("deletar");
        result.innerHTML = "feito";
    }
  },
}
</script>

