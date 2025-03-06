<template>
  <section id="hero" class="section">
    <h1>Hello, I'm <span class="name">Your Name</span></h1>
    <p>Web Developer | Vue.js Enthusiast</p>
    <button class="btn">View My Work</button>
  </section>
</template>

<style scoped>
.hero {
  text-align: center;
  padding: 4rem 0;
  background: var(--section-bg); /* Use the theme color */
  color: var(--text-color);
  width: 100%;
  min-height: 50vh; /* Ensure it takes up visible space */
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.name {
  display: inline-block;
  font-weight: bold;
}

.btn {
  background: var(--nav-bg);
  color: var(--text-color);
  padding: 0.8rem 1.5rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-weight: bold;
  margin-top: 1rem;
}

.btn:hover {
  background: #a7a5ad; /* Slightly darker Pewter */
}

@media (max-width: 768px) {
  .hero {
    padding: 2rem 1rem;
  }
}
</style>
