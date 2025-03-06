<template>
  <div id="app">
    <Navbar />
    <main>
      <ProfileContent />
      <Guestbook />
      <ContactForm />
    </main>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import Guestbook from './components/Guestbook.vue';
import ProfileContent from './components/ProfileContent.vue';

export default {
  components: {
    Navbar,
    ProfileContent,
    Guestbook
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
