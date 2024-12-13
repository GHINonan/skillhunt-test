<script setup>
import { requiredValidator, emailValidator } from '@/utils/validators'
import { ref } from 'vue'

const loading = ref(false)
function load() {
  loading.value = true
  setTimeout(() => (loading.value = false), 3000)
}

const visible = ref(false)

const refVForm = ref()

const formDataDefault = {
  email: '',
  password: '',
}
const formData = ref({ ...formDataDefault })

const onLogin = () => {
  alert(formData.value)
}

const onFormSubmit = () => {
  refVForm.value?.validate().then(({ valid }) => {
    if (valid) onLogin()
  })
}
</script>
<template>
  <v-form ref="refVForm" @submit.prevent="onFormSubmit">
    <v-text-field
      v-model="formData.email"
      label="Email Address"
      variant="outlined"
      prepend-icon="mdi-email"
      :rules="[requiredValidator, emailValidator]"
    ></v-text-field>

    <v-text-field
      v-model="formData.password"
      prepend-icon="mdi-lock"
      label="Password"
      variant="outlined"
      :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
      :type="visible ? 'text' : 'password'"
      @click:append-inner="visible = !visible"
      :rules="[requiredValidator]"
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
