<template>
  <div :class="theme">
    <Navbar @toggle-theme="toggleTheme" :theme="theme" />
    <main>
      <HeroSection />
      <AboutMe />
      <Projects />
      <Guestbook />
      <ContactForm />
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import Navbar from './components/Navbar.vue';
import HeroSection from './components/HeroSection.vue';
import AboutMe from './components/AboutMe.vue';
import Projects from './components/Projects.vue';
import Guestbook from './components/Guestbook.vue';
import ContactForm from './components/ContactForm.vue';

const theme = ref(localStorage.getItem('theme') || 'light');

const toggleTheme = () => {
  theme.value = theme.value === 'light' ? 'dark' : 'light';
  localStorage.setItem('theme', theme.value);
  document.body.className = theme.value; // Apply theme to body
};

onMounted(() => {
  document.body.className = theme.value;
});
</script>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  gap: 50px;
  padding: 20px;
  max-width: 1200px;
  margin: auto;
  scroll-behavior: smooth;
}

.dark {
  background: #1e293b;
  color: #f8fafc;
}

.light {
  background: #f8fafc;
  color: #1e293b;
}
</style>