<template>
  <section>
    <h2>Contact Me</h2>
    <form @submit.prevent="sendMessage">
      <input v-model="name" placeholder="Your Name" required />
      <input v-model="email" placeholder="Your Email" required />
      <textarea v-model="message" placeholder="Your Message" required></textarea>
      <button type="submit">Send</button>
    </form>
  </section>
</template>

<script setup>
import { ref } from "vue";

const name = ref("");
const email = ref("");
const message = ref("");

const sendMessage = () => {
  alert(`Message sent by ${name.value}`);
  name.value = "";
  email.value = "";
  message.value = "";
};
</script>
