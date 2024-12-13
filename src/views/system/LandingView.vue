<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row>
        <v-col cols="12" md="6" class="mx-auto pt-15">
          <v-card class="mx-auto text-center" subtitle="Your No.1 choice for Public Outsourcing!">
            <template #title>
              <h3 class="font-weight-black text-center">Welcome to SkillHunt</h3>
            </template>

            <v-card-text>
              SkillHunt offers a range of talented individuals with a unique set of skills that help
              you for any needs. We also provide you a platform to advertise and sell their own
              skills and expertise.<br /><br />
              Sign up or Log in today!
            </v-card-text>
            <v-card-actions class="justify-center pb-5">
              <v-btn variant="outlined" width="45%"> Sign Up </v-btn>
              <v-btn variant="outlined" width="45%"> Log In </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
</template>
