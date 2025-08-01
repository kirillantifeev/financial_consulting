<template>
  <form @submit.prevent="submitForm" class="form">
    <div class="form-group">
      <UiFormInput
        v-model="form.username"
        @blur="v$.username.$touch()"
        placeholder="john david"
        :error-message="v$.username.$errors[0]?.$message"
      >
        Full Name
      </UiFormInput>

      <UiFormInput
        v-model="form.email"
        @blur="v$.email.$touch()"
        placeholder="consult@mail.com"
        :error-message="v$.email.$errors[0]?.$message"
      >
        Email
      </UiFormInput>
    </div>

    <div class="form-group">
      <UiFormInput
        v-model="form.phone"
        @blur="v$.phone.$touch()"
        placeholder="+008 654 231"
        :error-message="v$.phone.$errors[0]?.$message"
      >
        Phone
      </UiFormInput>

      <UiFormInput
        v-model="form.company"
        @blur="v$.company.$touch()"
        placeholder="Company (optional)"
      >
        Company (optional)
      </UiFormInput>
    </div>

    <div class="form-group">
      <UiFormInput
        v-model="form.message"
        @blur="v$.message.$touch()"
        placeholder="Briefly tell us about your project and your current goals. How can we help you?"
        :error-message="v$.message.$errors[0]?.$message"
        multiline
      >
        Message
      </UiFormInput>
    </div>

    <UiButtonForm type="submit" :disabled="v$.$invalid">Send Message</UiButtonForm>
  </form>
</template>

<script setup lang="ts">
import { reactive } from 'vue';
import { useVuelidate } from '@vuelidate/core';
import { required, email, helpers } from '@vuelidate/validators';
import UiFormInput from './UI/UiFormInput.vue';
import UiButtonForm from './UI/UiButtonForm.vue';

interface FormData {
  username: string;
  email: string;
  phone: string;
  company: string;
  message: string;
}

const form = reactive<FormData>({
  username: '',
  email: '',
  phone: '',
  company: '',
  message: ''
});

const rules = {
  username: {
    required: helpers.withMessage('Full name is required', required),
    english: helpers.withMessage(
      'Only English letters allowed',
      (value: string) => /^[A-Za-z\s]+$/.test(value)
    ),
    minLength: helpers.withMessage(
      'Minimum 3 characters required',
      (value: string) => value.length >= 3
    )
  },
  email: {
    required: helpers.withMessage('Email is required', required),
    email: helpers.withMessage('Please enter a valid email', email)
  },
  phone: {
    required: helpers.withMessage('Phone number is required', required),
    phone: helpers.withMessage(
      'Invalid phone number format',
      (value: string) => /^[+\d\s()-]{10,20}$/.test(value)
    )
  },
  company: {}, 
  message: {
    required: helpers.withMessage('Message is required', required),
    minLength: helpers.withMessage(
      'Minimum 10 characters required',
      (value: string) => value.length >= 10
    )
  }
};

const v$ = useVuelidate(rules, form);

const submitForm = async () => {
  const isValid = await v$.value.$validate();
  if (isValid) {
    console.log('Form submitted:', form);
  }
};
</script>

<style scoped>
    .form {
        width: 100%;
        padding-right: 22.37px;
        display: flex;
        flex-direction: column;
        gap: 28px;
    }

    .form-group {
        display: flex;
        gap: 24px;
    }

    @media (max-width: 650px) {
        .form-group {
            flex-direction: column;
        }
    }
</style>