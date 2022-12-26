<template>
  <q-page class="">
    <div class="row ">
      <div class="col-4 col-md-4 col-lg-4 col-sm-12 col-xs-12 q-pa-xl">
        <div class="text-center q-mt-lg">
          <q-img
            class="logo"
            src="~/src/assets/logo.jpg"
          />
        </div>
        <div class="text-h4 text-bold">Blogging Site</div>
        <div class="text-grey-7">Please Log in</div>
        <div class="column">
          <q-input
            class="q-mt-sm"
            outlined
            v-model="form.email.value"
            @update:model-value="validateInput(form, 'email')"
            @blur="validateInput(form, 'email')"
            label="Enter your email"
            :error="form.email.error"
            :error-message="form.email.msg">
            <template v-slot:prepend>
              <q-icon name="email"></q-icon>
            </template>
          </q-input>
          <q-input
            class="q-mt-sm"
            outlined
            label="Enter your password"
            v-model="form.password.value"
            @update:model-value="validateInput(form, 'password')"
            @blur="validateInput(form, 'password')"
            :type="!isPassword ? 'password' : 'text' "
            :error="form.password.error"
            :error-message="form.password.msg">
            <template v-slot:prepend>
              <q-icon name="lock"></q-icon>
            </template>
            <template v-slot:append>
              <q-icon
              @click="isPassword = !isPassword"
              :name="!isPassword ? 'visibility_off' : 'visibility' "
              />
            </template>
          </q-input>
          <div class="column">
            <q-btn
              class="q-mt-sm"
              :disable="!isSubmitBtn(form)"
              :color="!isSubmitBtn(form) ? 'grey-6':'indigo'"
              @click="submitLogin"
            >
              Login
            </q-btn>
          </div>
        </div>
      </div>
      <div class="col-8 col-md-8 col-lg-8 col-sm-12 col-xs-12 text-center q-mt-xl">
        <p class="text-h4">Text Here</p>
        <p class="text-p">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Mollitia aliquam, assumenda quia nemo esse quibusdam placeat quae? Magnam ab tenetur numquam magni voluptate, veniam ea doloremque vitae, nesciunt animi beatae?</p>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import Hooks from 'src/hooks'
import { ref } from 'vue'
const { isFormValid, validateInput, isSubmitBtn } = Hooks()
const isPassword = ref()
const form = ref({
  email: {
    value: '',
    required: true,
    requiredMsg: 'Email is required.',
    emailMsg: 'Invalid email address',
    email: true
  },
  password: {
    value: '',
    requiredMsg: 'Password is required.',
    required: true
  }
})

const submitLogin = () => {
  if (!isFormValid) return false
}
</script>
<style>
.logo{
  width: 50%;
  height: 50%;
  border-radius: 100%;
}
</style>
