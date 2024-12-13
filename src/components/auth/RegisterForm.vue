<script setup>
import {
  requiredValidator,
  emailValidator,
  passwordValidator,
  confirmedValidator,
} from '@/utils/validators'
import { ref } from 'vue'

const visible = ref(false)
const confirmVisible = ref(false)
const refVForm = ref()

const formDataDefault = {
  firstname: '',
  lastname: '',
  email: '',
  password: '',
  password_confirmation: '',
}

const formData = ref({
  ...formDataDefault,
})

const onRegister = () => {
  alert(formData.value.email)
}

const onFormSubmit = () => {
  refVForm.value?.validate().then(({ valid }) => {
    if (valid) onRegister()
  })
}
</script>

<template>
  <v-form ref="refVForm" @submit.prevent="onFormSubmit">
    <v-row>
      <v-col cols="12" md="6">
        <v-text-field
          v-model="formData.firstname"
          prepend-icon="mdi-account"
          label="First Name"
          variant="outlined"
          :rules="[requiredValidator]"
        ></v-text-field
      ></v-col>
      <v-col cols="12" md="6"
        ><v-text-field
          v-model="formData.lastname"
          label="Last Name"
          variant="outlined"
          :rules="[requiredValidator]"
        ></v-text-field
      ></v-col>
      <v-col cols="12"
        ><v-text-field
          v-model="formData.email"
          label="Email Address"
          variant="outlined"
          prepend-icon="mdi-email"
          :rules="[requiredValidator, emailValidator]"
        ></v-text-field
      ></v-col>
      <v-col cols="12"
        ><v-text-field
          v-model="formData.password"
          label="Enter Password"
          variant="outlined"
          prepend-icon="mdi-lock"
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          @click:append-inner="visible = !visible"
          :rules="[requiredValidator, passwordValidator]"
        ></v-text-field
      ></v-col>
      <v-col cols="12"
        ><v-text-field
          v-model="formData.password_confirmation"
          label="Enter Password Again to Confirm"
          variant="outlined"
          prepend-icon="mdi-lock-check"
          :append-inner-icon="confirmVisible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="confirmVisible ? 'text' : 'password'"
          @click:append-inner="confirmVisible = !confirmVisible"
          :rules="[
            requiredValidator,
            confirmedValidator(formData.password_confirmation, formData.password),
          ]"
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
