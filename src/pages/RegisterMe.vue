<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

// Form data
const name = ref('')
const email = ref('')
const password = ref('')
const isLoading = ref(false)

const handleSubmit = () => {
  // Basic form validation
  if (name.value && email.value && password.value) {
    isLoading.value = true
    // Simulate API call
    setTimeout(() => {
      isLoading.value = false
      router.push('/login')  // Redirect to login after successful registration
    }, 1000)
  } else {
    // You can show an error message if the fields are empty
    alert('Please fill in all fields!')
  }
}
</script>

<template>
  <q-page padding>
    <q-card>
      <q-card-section>
        <div class="text-h6">Register</div>
        <div class="q-mt-md">
          <q-input
            filled
            v-model="name"
            label="Name"
            autofocus
            :rules="[val => val && val.length > 0 || 'Name is required']"
          />
        </div>
        <div class="q-mt-md">
          <q-input
            filled
            v-model="email"
            label="Email"
            type="email"
            :rules="[val => val && val.length > 0 || 'Email is required']"
          />
        </div>
        <div class="q-mt-md">
          <q-input
            filled
            v-model="password"
            label="Password"
            type="password"
            :rules="[val => val && val.length > 0 || 'Password is required']"
          />
        </div>
        <div class="q-mt-md">
          <q-btn
            label="Register"
            color="primary"
            @click="handleSubmit"
            :loading="isLoading"
            class="full-width"
          />
        </div>
      </q-card-section>
    </q-card>
    <div class="q-mt-md text-center">
      <span>Already have an account? </span>
      <q-btn flat label="Login" to="/login" />
    </div>
  </q-page>
</template>


