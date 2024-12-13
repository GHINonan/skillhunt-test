<script setup>
import {
  requiredValidator,
  emailValidator,
  passwordValidator,
  confirmedValidator,
} from '@/utils/validators'
import { ref } from 'vue'
import AlertNotification from '@/components/common/AlertNotification.vue'
import { supabase, formActionDefault } from '@/utils/supabase.js'

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

const formAction = ref({
  ...formActionDefault,
})

const onRegister = async () => {
  formAction.value = { ...formActionDefault }
  formAction.value.formProcess = true

  const { data, error } = await supabase.auth.signUp({
    email: formData.value.email,
    password: formData.value.password,
    options: {
      data: {
        firstname: formData.value.firstname,
        lastname: formData.value.lastname,
      },
    },
  })

  if (error) {
    console.log(error)
    formAction.value.formErrorMessage = error.message
    formAction.value.formStatus = error.status
  } else if (data) {
    console.log(data)
    formAction.value.formSuccessMessage =
      'Congratulations! You have successfully registered your account!'
    refVForm.value?.reset()
  }

  formAction.value.formProcess = false
}

const onFormSubmit = () => {
  refVForm.value?.validate().then(({ valid }) => {
    if (valid) onRegister()
  })
}
</script>

<template>
  <AlertNotification
    :form-success-message="formAction.formSuccessMessage"
    :form-error-message="formAction.formErrorMessage"
  ></AlertNotification>

  <v-form class="mt-5" ref="refVForm" @submit.prevent="onFormSubmit">
    <v-row>
      <v-col cols="12" md="6">
        <v-text-field
          v-model="formData.firstname"
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
      :disabled="formAction.formProcess"
      :loading="formAction.formProcess"
      >Register</v-btn
    ></v-form
  >
</template>
