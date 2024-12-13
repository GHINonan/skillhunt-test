<script setup>
import { ref } from 'vue'

const visible = ref(false)
</script>

<template>
  <v-form fast-fail @submit.prevent>
    <v-row>
      <v-col cols="12" md="6">
        <v-text-field
          prepend-icon="mdi-account"
          label="First Name"
          variant="outlined"
        ></v-text-field
      ></v-col>
      <v-col cols="12" md="6"
        ><v-text-field label="Last Name" variant="outlined"></v-text-field
      ></v-col>
      <v-col cols="12"
        ><v-text-field
          label="Email Address"
          variant="outlined"
          prepend-icon="mdi-email"
        ></v-text-field
      ></v-col>
      <v-col cols="12"
        ><v-text-field
          label="Enter Password"
          variant="outlined"
          prepend-icon="mdi-lock"
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          @click:append-inner="visible = !visible"
        ></v-text-field
      ></v-col>
      <v-col cols="12"
        ><v-text-field
          label="Enter Password Again to Confirm"
          variant="outlined"
          prepend-icon="mdi-lock-check"
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          @click:append-inner="visible = !visible"
        ></v-text-field
      ></v-col>
    </v-row>

    <v-btn
      class="mt-2"
      type="submit"
      block
      variant="outlined"
      rounded="lg"
      prepend-icon="mdi-account-plus"
      >Register</v-btn
    ></v-form
  >
</template>
