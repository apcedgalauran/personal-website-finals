<template>
  <nav class="navbar">
    <div class="container">
      <h1 class="logo">My Personal Website</h1>
      <div class="hamburger" @click="toggleMenu">☰</div>
      <ul :class="{ 'show': isMenuOpen }">
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#gallery">Gallery</a></li>
        <li><a href="#guestbook">Guestbook</a></li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isMenuOpen: false
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    }
  }
};
</script>

<style>
/* Navbar styles */
.navbar {
  background: #1e1e1e;
  padding: 1rem 1.5rem;
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  z-index: 1000;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.navbar .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: auto;
  padding: 0 20px;
}

.navbar .logo {
  font-size: 1.5rem;
  font-weight: bold;
  color: #f8f9fa;
}

/* Default navigation menu */
.navbar ul {
  list-style: none;
  display: flex;
  gap: 20px;
  align-items: center;
}

/* Navbar links */
.navbar a {
  color: #f0f0f0;
  font-weight: bold;
  font-size: 1rem;
  padding: 10px 14px;
  transition: all 0.3s ease-in-out;
  border-radius: 6px;
  text-decoration: none; /* This removes the underline */
}

/* Hover effect without underline */
.navbar a:hover {
  background: rgba(255, 165, 0, 0.2);
  color: #ffa500;
}

/* Mobile responsive */
@media (max-width: 768px) {
  .navbar {
    padding: 0.8rem 1rem;
  }

  .navbar .logo {
    font-size: 1.3rem;
  }

  /* Hide menu by default */
  .navbar ul {
    display: none;
    flex-direction: column;
    position: absolute;
    top: 60px;
    left: 0;
    width: 100%;
    background: #1e1e1e;
    padding: 10px 0;
    text-align: center;
  }

  /* Show menu when active */
  .navbar ul.show {
    display: flex;
  }

  .navbar a {
    display: block;
    padding: 12px 0;
    font-size: 1rem;
  }

  /* Hamburger menu */
  .hamburger {
    display: block;
    font-size: 1.8rem;
    color: white;
    cursor: pointer;
  }
}

/* Hide hamburger menu on larger screens */
@media (min-width: 769px) {
  .hamburger {
    display: none;
  }
}
</style>