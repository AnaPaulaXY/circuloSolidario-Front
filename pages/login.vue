<template>
<div class="body">
    <barra-nav></barra-nav>
      <main id="conteudo">
        <h1>Login</h1>
        <div>
            <form @submit.prevent="userLogin">
              <div>
                <label>Nome</label>
                <input type="text" v-model="login.username" />
              </div>
              <div>
                <label>Senha</label>
                <input type="text" v-model="login.password" />
              </div>
              <div>
                <button type="submit">Entrar</button>
              </div>
            </form>
  </div>
      </main>
    <barra-footer></barra-footer>
  </div>
</template>

<script>
import barraNav from '~/components/barraNav.vue'
import barraFooter from '~/components/barraFooter.vue'

export default {
  data() {
    return {
      login: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('local', { data: this.login })
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>