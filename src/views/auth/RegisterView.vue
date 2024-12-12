<script>
import { ref } from 'vue'

const theme = ref('light')

function onClick() {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
}
</script>

<template>
  <v-responsive class="border rounded">
    <v-app :theme="theme">
      <v-app-bar class="px-3">
        <v-spacer></v-spacer>

        <v-btn
          :prepend-icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
          text="Toggle Theme"
          slim
          @click="onClick"
        ></v-btn>
      </v-app-bar>

      <v-main>
        <v-container>
          <v-row>
            <v-col cols="12" md="6" class="mx-auto">
              <h1 class="text-center">SkillHunt</h1>
              <p class="text-center">Your No.1 Choice for Public Outsourcing!</p>
              <br />
              <v-card class="mx-auto, text-center" prepend-icon="mdi-account">
                <template v-slot:title>
                  <span class="font-weight-black">Create an Account</span>
                </template>

                <v-card-text class="bg-surface-light pt-4">
                  <v-form fast-fail @submit.prevent>
                    <!--<v-row>
                      <v-col></v-col>
                      <v-col></v-col> </v-row
                    >/-->
                    <v-text-field label="First Name" variant="outlined"></v-text-field>
                    <v-text-field label="Last Name" variant="outlined"></v-text-field>
                    <v-text-field label="Email Address" variant="outlined"></v-text-field>
                    <v-text-field
                      label="Enter Password"
                      type="password"
                      variant="outlined"
                    ></v-text-field>
                    <v-text-field
                      label="Enter Password Again to Confirm"
                      type="password"
                      variant="outlined"
                    ></v-text-field>
                    <v-btn class="mt-2" type="submit" block>Register</v-btn>
                    <v-divider class="my-4"></v-divider>
                    <h5>
                      Already have an account?
                      <RouterLink to="/login">Click Here To Log In!</RouterLink>
                    </h5>
                  </v-form>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-main>
    </v-app>
  </v-responsive>
</template>
