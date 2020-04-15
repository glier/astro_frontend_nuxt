<template>
  <v-container fluid fill-height>
    <v-row align="center" justify="center">
      <v-col cols="12" sm="8" md="8">
        <v-card class="elevation-2 ma-3" outlined>
          <v-row no-gutters>
            <v-col cols="6">
              <LoginForm />
            </v-col>
            <v-col cols="6" style="background-color: #f9f9f9;">
              <SocialAuthButtons />
            </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import LoginForm from '../components/authentication/LoginForm'
import SocialAuthButtons from '../components/authentication/SocialAuthButtons'

export default {
  name: 'Login',
  components: {
    LoginForm,
    SocialAuthButtons
  }
}
</script>

<style scoped>

</style>
