<template>
  <v-container>
    <v-card-title>
      Создать аккаунт
    </v-card-title>
    <v-card-text class="pb-0">
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field
          v-model="email"
          label="E-mail"
          name="email"
          prepend-icon="mdi-account-circle-outline"
          type="text"
          :rules="emailRules"
        />
        <v-text-field
          v-model="password"
          label="Password"
          name="password"
          prepend-icon="mdi-lock"
          type="password"
          :rules="passwordRules"
        />
        <v-checkbox v-model="checkboxPolicy" :rules="policyRules" required>
          <template v-slot:label>
            <div>
              Я прочитал и согласен с
              <v-tooltip bottom>
                <template v-slot:activator="{ on }">
                  <a
                    target="_blank"
                    href="http://vuetifyjs.com"
                    @click.stop
                    v-on="on"
                  >
                    Политика конфиденциальности
                  </a>
                </template>
                Откроется в новом окне
              </v-tooltip>
              и
              <v-tooltip bottom>
                <template v-slot:activator="{ on }">
                  <a
                    target="_blank"
                    href="http://vuetifyjs.com"
                    @click.stop
                    v-on="on"
                  >
                    Права Использования
                  </a>
                </template>
                Откроется в новом окне
              </v-tooltip>
              , об использовании моих личных данных.
            </div>
          </template>
        </v-checkbox>
      </v-form>
    </v-card-text>
    <v-card-actions>
      <v-container>
        <v-btn
          block
          color="primary"
          :disabled="!valid"
          @click="fetchRegistration"
        >
          Регистрация
        </v-btn>

        <p class="text-center mt-4">
          <span>У вас уже есть аккаунт? <nuxt-link to="/login">Войти</nuxt-link></span>
        </p>
      </v-container>
    </v-card-actions>
  </v-container>
</template>

<script>
export default {
  name: 'RegistrationForm',
  data () {
    return {
      valid: true,
      checkboxPolicy: false,
      email: '',
      password: '',
      errMessage: '',
      emailRules: [
        v => !!v || 'Требуется электронная почта',
        v => /.+@.+\..+/.test(v) || 'E-mail должен быть действительным',
        v => (this.errMessage.length === 0) || 'E-mail уже используется!'
      ],
      passwordRules: [
        v => !!v || 'Необходим пароль',
        v => (v && v.length >= 6) || 'Пароль должен быть больше 6 символов'
      ],
      policyRules: [
        v => !!v || 'Вы должны согласиться!'
      ]
    }
  },
  methods: {
    validate () {
      return this.$refs.form.validate()
    },
    async fetchRegistration () {
      if (this.validate()) {
        try {
          await this.$axios.post('api/auth/signup', {
            email: this.email,
            password: this.password,
            isPolicyAgree: this.checkboxPolicy
          }).then((response) => {
            this.$auth.loginWith('local', { data: { email: this.email, password: this.password } })
          }).catch((error) => {
            if (error.response.status === 400 && error.response.data.message === 'Error: Email is already in use!') {
              this.errMessage = error.response.data.message
              this.validate()
              this.errMessage = ''
            }
          })
        } catch (err) {
          // this.errMessage = response.message
          // console.log(this.errMessage)
        }
      }
    }
  }
}
</script>

<style scoped>

</style>
