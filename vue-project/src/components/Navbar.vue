<template>
  <nav class="navbar">
    <div class="container">
      <h1 class="logo">My Portfolio</h1>
      <ul>
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/about">About</router-link></li>
        <li><router-link to="/projects">Projects</router-link></li>
        <li><router-link to="/contact">Contact</router-link></li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  background: #333;
  padding: 1rem;
}

.navbar .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navbar ul {
  list-style: none;
  display: flex;
  gap: 20px;
}

.navbar a {
  text-decoration: none;
  color: white;
  font-weight: bold;
}

.navbar a:hover {
  color: var(--primary-color);
}

@media (max-width: 768px) {
  .navbar ul {
    flex-direction: column;
  }
}
</style>
