<template>
  <v-container>
    <v-card-title>
      С возвращением!
    </v-card-title>
    <v-card-text>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field
          v-model="login.email"
          label="Email"
          name="email"
          prepend-icon="mdi-account-circle-outline"
          type="text"
          :rules="emailRules"
        />
        <v-text-field
          v-model="login.password"
          label="Password"
          name="password"
          prepend-icon="mdi-lock"
          type="password"
          :rules="passwordRules"
          @keyup.enter="userLogin"
        />
      </v-form>
    </v-card-text>
    <v-card-actions>
      <v-container>
        <v-btn
          block
          color="primary"
          @click="userLogin"
        >
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
      valid: true,
      isError: false,
      errStatus: 0,
      emailRules: [
        v => !!v || 'Требуется электронная почта',
        v => /.+@.+\..+/.test(v) || 'E-mail должен быть действительным',
        v => (!this.isError && this.errStatus === 0) || 'Ошибка: ' + this.errStatus,
        v => (!this.isError) || 'Неверный E-mail или пароль'

      ],
      passwordRules: [
        v => !!v || 'Необходим пароль',
        v => (!this.isError && this.errStatus === 0) || 'Ошибка: ' + this.errStatus,
        v => (!this.isError) || 'Неверный E-mail или пароль'
      ],
      login: {
        email: '',
        password: ''
      }
    }
  },
  methods: {
    async userLogin () {
      if (this.validate()) {
        try {
          await this.$auth.loginWith('local', { data: this.login })
            .then(() => {
              this.clearFields()
            })
            .catch((error) => {
              if (error.response.status === 401) {
                this.isError = true
                this.validate()
                this.isError = false
              } else {
                this.isError = true
                this.errStatus = error.response.status
                this.validate()
                this.isError = false
                this.errStatus = 0
              }
            })
        } catch (err) {
          // console.log(err)
        }
      }
    },
    clearFields () {
      this.login.email = ''
      this.login.password = ''
    },
    validate () {
      return this.$refs.form.validate()
    }
  }
}
</script>

<style scoped>

</style>
