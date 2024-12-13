<script setup>
import { ref } from 'vue'

const loading = ref(false)
function load() {
  loading.value = true
  setTimeout(() => (loading.value = false), 3000)
}

const visible = ref(false)
</script>
<template>
  <v-form fast-fail @submit.prevent>
    <v-text-field label="Email Address" variant="outlined" prepend-icon="mdi-email"></v-text-field>

    <v-text-field
      prepend-icon="mdi-lock"
      label="Password"
      variant="outlined"
      :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
      :type="visible ? 'text' : 'password'"
      @click:append-inner="visible = !visible"
    ></v-text-field>
    <v-btn
      :loading="loading"
      class="mt-2"
      type="submit"
      block
      variant="outlined"
      rounded="lg"
      prepend-icon="mdi-login"
      @click="load"
      >Log In</v-btn
    >
  </v-form>
</template>
