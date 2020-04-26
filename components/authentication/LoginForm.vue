<template>
  <v-container>
    <v-card-title>
      С возвращением!
    </v-card-title>
    <v-card-text>
      <v-form>
        <v-text-field
          v-model="login.username"
          label="Login"
          name="login"
          prepend-icon="mdi-account-circle-outline"
          type="text"
        />
        <v-text-field
          v-model="login.password"
          label="Password"
          name="password"
          prepend-icon="mdi-lock"
          type="password"
        />
      </v-form>
    </v-card-text>
    <v-card-actions>
      <v-container>
        <v-btn block color="primary" @click="userLogin" @keyup.enter="userLogin">
          Войти
        </v-btn>
        <v-spacer />
        <p class="text-center mt-4">
          <a href="#">
            Забыли пароль?
          </a>
        </p>
        <p class="text-center">
          <span>Не зарегистрированы?
            <nuxt-link to="/signup">
              Sign Up
            </nuxt-link>
          </span>
        </p>
      </v-container>
    </v-card-actions>
  </v-container>
</template>

<script>
export default {
  name: 'LoginForm',
  data () {
    return {
      login: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    async userLogin () {
      try {
        await this.$auth.loginWith('local', { data: this.login })
      } catch (err) {
        // console.log(err)
      }
    }
  }
}
</script>

<style scoped>

</style>
