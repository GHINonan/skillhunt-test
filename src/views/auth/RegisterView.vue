<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import RegisterForm from '@/components/auth/RegisterForm.vue'
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row>
        <v-col cols="12" md="6" class="mx-auto pt-10">
          <v-card class="mx-auto, text-center" variant="outlined" subtitle="Create an Account">
            <template v-slot:title>
              <h2 class="font-weight-black">SkillHunt</h2>
            </template>

            <v-card-text class="bg-surface-light pt-4">
              <v-divider class="my-4"></v-divider>
              <RegisterForm></RegisterForm>
              <v-divider class="my-4"></v-divider>
              <h5>
                Already have an account?
                <RouterLink to="/login">Click Here To Log In!</RouterLink>
              </h5>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
</template>
