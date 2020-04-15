<template>
  <v-container fluid fill-height>
    <v-card-text>
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
      <v-btn
        class="my-5"
        color="#4285f4"
        v-bind:disabled="!checkboxPolicy"
        large
        block>
        <v-avatar left size="36" class="mx-auto">
          <v-img src="google.svg"></v-img>
        </v-avatar>
        <v-divider
          class="mx-4"
          vertical
        ></v-divider>
        Войти через Google
      </v-btn>
      <v-btn
        class="mb-5"
        color="#3b5998"
        v-bind:disabled="!checkboxPolicy"
        large
        block>
        <v-avatar left size="36" class="mx-auto">
          <v-img src="facebook.svg"></v-img>
        </v-avatar>
        <v-divider
          class="mx-4"
          vertical
        ></v-divider>
        Войти через Facebook
      </v-btn>
    </v-card-text>
  </v-container>
</template>

<script>
export default {
  name: 'SocialAuthButtons',
  data () {
    return {
      checkboxPolicy: false
    }
  }
}
</script>

<style scoped>

</style>
