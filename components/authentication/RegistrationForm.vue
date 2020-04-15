<template>
  <v-container>
    <v-card-title>
      Создать аккаунт
    </v-card-title>
    <v-card-text class="pb-0">
      <v-form>
        <v-text-field
          label="E-mail"
          name="email"
          prepend-icon="mdi-account-circle-outline"
          type="text"
        />
        <v-text-field
          label="Password"
          name="password"
          prepend-icon="mdi-lock"
          type="password"
        />
        <v-checkbox v-model="checkboxPolicy">
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

        <v-btn block color="primary" v-bind:disabled="!checkboxPolicy">Регистрация</v-btn>

        <p class="text-center mt-4"><span>У вас уже есть аккаунт? <nuxt-link to="/login">Войти</nuxt-link></span></p>
      </v-container>
    </v-card-actions>
  </v-container>
</template>

<script>
export default {
  name: 'RegistrationForm',
  data () {
    return {
      checkboxPolicy: false
    }
  }
}
</script>

<style scoped>

</style>
