<template>
  <section class="hero">
    <h1>Hello, I'm <span class="name">Your Name</span></h1>
    <p>Web Developer | Vue.js Enthusiast</p>
    <button class="btn">View My Work</button>
  </section>
</template>

<style scoped>
.hero {
  text-align: center;
  padding: 4rem 0;
  background: #ffffff;
  color: white;
}

.name {
  display: inline-block;
}

@media (max-width: 768px) {
  .hero {
    padding: 2rem 0;
  }
}
</style>
