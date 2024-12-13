<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import LoginForm from '@/components/auth/LogInForm.vue'
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row>
        <v-col cols="12" md="6" class="mx-auto pt-14">
          <h1 class="text-center">SkillHunt</h1>
          <p class="text-center">Your No.1 Choice for Public Outsourcing!</p>
          <br />
          <v-card class="mx-auto, text-center" prepend-icon="mdi-account" variant="outlined">
            <template v-slot:title>
              <span class="font-weight-black">Please Log In to Continue</span>
            </template>

            <v-card-text class="bg-surface-light pt-4">
              <v-divider class="my-4"></v-divider>
              <LoginForm></LoginForm>
              <v-divider class="my-4"></v-divider>
              <h5>
                No account?
                <RouterLink to="/register">Click here to Register instead!</RouterLink>
              </h5>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
  <
</template>
