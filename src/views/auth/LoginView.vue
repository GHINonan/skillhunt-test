<script setup>
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
          variant="tonal"
          :prepend-icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
          text="Toggle Theme"
          slim
          @click="onClick"
        ></v-btn>
      </v-app-bar>

      <v-main>
        <v-container>
          <v-row>
            <v-col cols="12">
              <h1 class="text-center">SkillHunt</h1>
              <p class="text-center">Your No.1 Choice for Public Outsourcing!</p>
              <br />
              <v-card class="mx-auto, text-center">
                <template v-slot:title>
                  <span class="font-weight-black">Please Log In to Continue</span>
                </template>

                <v-card-text class="bg-surface-light pt-4">
                  <v-sheet class="mx-auto">
                    <v-form fast-fail @submit.prevent>
                      <v-text-field label="First name"></v-text-field>

                      <v-text-field label="Last name"></v-text-field>

                      <v-btn class="mt-2" type="submit" block>Submit</v-btn>
                    </v-form>
                  </v-sheet>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-main>
      <v-footer border app
        >"When you have the chance to make a choice, make one that you know you won't
        regret."</v-footer
      >
    </v-app>
  </v-responsive>
</template>
