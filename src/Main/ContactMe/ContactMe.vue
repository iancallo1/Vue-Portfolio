<script setup>
import { ref } from 'vue'

const formData = ref({
  name: '',
  email: '',
  message: ''
})

const handleSubmit = () => {
  // Here you would typically handle the form submission
  console.log('Form submitted:', formData.value)
  // Reset form after submission
  formData.value = {
    name: '',
    email: '',
    message: ''
  }
}
</script>

<template>
  <div class="contact-form-container">
    <form @submit.prevent="handleSubmit" class="max-w-md mx-auto bg-gray-900 p-8 rounded-lg shadow-xl">
      <h2 class="text-3xl font-bold mb-6 text-white text-center">Get in Touch</h2>
      
      <div class="mb-6">
        <label for="name" class="block text-sm font-medium text-gray-400 mb-2">Name</label>
        <input
          type="text"
          id="name"
          v-model="formData.name"
          class="w-full px-4 py-2 bg-gray-800 border border-gray-700 rounded-md text-white focus:outline-none focus:border-blue-500 transition-colors"
          required
        />
      </div>

      <div class="mb-6">
        <label for="email" class="block text-sm font-medium text-gray-400 mb-2">Email</label>
        <input
          type="email"
          id="email"
          v-model="formData.email"
          class="w-full px-4 py-2 bg-gray-800 border border-gray-700 rounded-md text-white focus:outline-none focus:border-blue-500 transition-colors"
          required
        />
      </div>

      <div class="mb-6">
        <label for="message" class="block text-sm font-medium text-gray-400 mb-2">Message</label>
        <textarea
          id="message"
          v-model="formData.message"
          rows="4"
          class="w-full px-4 py-2 bg-gray-800 border border-gray-700 rounded-md text-white focus:outline-none focus:border-blue-500 transition-colors resize-none"
          required
        ></textarea>
      </div>

      <button
        type="submit"
        class="w-full bg-blue-600 hover:bg-blue-700 text-white font-medium py-2 px-4 rounded-md transition-colors duration-300 transform hover:scale-105"
      >
        Send Message
      </button>
    </form>
  </div>
</template>

<style scoped>
.contact-form-container {
  animation: slideUp 0.5s ease-out;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

input:-webkit-autofill,
input:-webkit-autofill:hover,
input:-webkit-autofill:focus,
textarea:-webkit-autofill,
textarea:-webkit-autofill:hover,
textarea:-webkit-autofill:focus {
  -webkit-text-fill-color: white;
  -webkit-box-shadow: 0 0 0px 1000px #1f2937 inset;
  transition: background-color 5000s ease-in-out 0s;
}
</style>
