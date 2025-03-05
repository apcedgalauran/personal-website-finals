<template>
  <nav class="navbar">
    <div class="container">
      <h1 class="logo">My Portfolio</h1>
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#guestbook">Guestbook</a></li>
        <li><a href="#contact">Contact</a></li>
        <li>
          <button @click="$emit('toggle-theme')" class="theme-toggle">
            Toggle Theme
          </button>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  background: #333;
  padding: 1rem;
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  z-index: 1000;
}

.navbar .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: auto;
  padding: 0 20px;
}

.navbar ul {
  list-style: none;
  display: flex;
  gap: 20px;
  align-items: center;
}

.navbar a {
  text-decoration: none;
  color: white;
  font-weight: bold;
  transition: color 0.3s;
}

.navbar a:hover {
  color: var(--primary-color, #4ade80);
}

.theme-toggle {
  background: transparent;
  border: 1px solid white;
  color: white;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 5px;
}

.theme-toggle:hover {
  background: rgba(255, 255, 255, 0.2);
}

@media (max-width: 768px) {
  .navbar ul {
    flex-direction: column;
    gap: 10px;
  }
}
</style>
