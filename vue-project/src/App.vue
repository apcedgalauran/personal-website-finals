<template>
  <div id="app">
    <Navbar />
    <main>
      <HeroSection />
      <AboutMe />
      <Projects />
      <Guestbook />
      <ContactForm />
    </main>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import HeroSection from './components/HeroSection.vue';
import AboutMe from './components/AboutMe.vue';
import Projects from './components/Projects.vue';
import Guestbook from './components/Guestbook.vue';
import ContactForm from './components/ContactForm.vue';

export default {
  components: {
    Navbar,
    HeroSection,
    AboutMe,
    Projects,
    Guestbook,
    ContactForm
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'Arial', sans-serif;
}
</style>
