<template>
  <v-container>
    <v-card-title>
      С возвращением!
    </v-card-title>
    <v-card-text>
      <v-form>
        <v-text-field
          label="Login"
          name="login"
          prepend-icon="mdi-account-circle-outline"
          type="text"
        />
        <v-text-field
          label="Password"
          name="password"
          prepend-icon="mdi-lock"
          type="password"
        />
      </v-form>
    </v-card-text>
    <v-card-actions>
      <v-container>
        <v-btn block color="primary">Войти</v-btn>
        <v-spacer/>
        <p class="text-center mt-4"><a href="#">Забыли пароль?</a></p>
        <p class="text-center"><span>Не зарегистрированы? <nuxt-link to="/signup">Sign Up</nuxt-link></span></p>
      </v-container>
    </v-card-actions>
  </v-container>
</template>

<script>
export default {
  name: 'LoginForm'
}
</script>

<style scoped>

</style>
