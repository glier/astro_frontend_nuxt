<template>
<!--  <v-container class="fill-height" fluid>-->
<!--    <v-row no-gutters align="center" justify="center">-->
<!--      <v-col>-->
<!--        <v-card-->
<!--            class="pa-2"-->
<!--            outlined-->
<!--            tile-->
<!--          >-->
<!--            Column 1-->
<!--          </v-card>-->
<!--        </v-col>-->
<!--      <v-col>-->
<!--        <v-card-->
<!--          class="pa-2"-->
<!--          outlined-->
<!--          tile-->
<!--        >-->
<!--          Column 2-->
<!--        </v-card>-->
<!--      </v-col>-->
<!--        </v-row>-->
<!--  </v-container>-->
  <v-container fluid fill-height>
    <v-row align="center" justify="center">
      <v-col xs="12" sm="12" md="8">
        <v-card class="elevation-2 ma-3" outlined>
          <v-row no-gutters>
            <v-col>
              <RegistrationForm />
            </v-col>
            <v-col style="background-color: #f9f9f9;">
              <SocialAuthButtons />
            </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import RegistrationForm from '../components/authentication/RegistrationForm'
import SocialAuthButtons from '../components/authentication/SocialAuthButtons'

export default {
  name: 'Login',
  components: {
    RegistrationForm,
    SocialAuthButtons
  }
}
</script>

<style scoped>

</style>
