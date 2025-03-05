<template>
  <section class="hero">
    <h1>Hello, I'm <span class="animated-name">Your Name</span></h1>
    <p>Web Developer | Vue.js Enthusiast</p>
    <button class="btn">View My Work</button>
  </section>
</template>

<style scoped>
.hero {
  text-align: center;
  padding: 4rem 0;
  background: #007bff;
  color: white;
}

.animated-name {
  display: inline-block;
  transition: transform 0.3s ease-in-out;
}

.animated-name:hover {
  transform: scale(1.1);
  color: yellow;
}

@media (max-width: 768px) {
  .hero {
    padding: 2rem 0;
  }
}
</style>
