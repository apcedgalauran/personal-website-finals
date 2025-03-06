<template>
  <nav class="navbar">
    <div class="container">
      <h1 class="logo">My Personal Website</h1>
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#gallery">Gallery</a></li>
        <li><a href="#guestbook">Guestbook</a></li>
        <li>

        </li>
      </ul>
    </div>
  </nav>
</template>

<style>
.navbar {
  background: #1e1e1e;
  padding: 1.2rem 1.5rem; /* Slightly more padding */
  position: relative;
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
  font-size: 1.75rem; /* Slightly larger */
  font-weight: bold;
  color: #f8f9fa;
}

.navbar ul {
  list-style: none;
  display: flex;
  gap: 24px; /* Slightly increased spacing */
  align-items: center;
}

.navbar a {
  text-decoration: none;
  color: #f0f0f0;
  font-weight: bold;
  font-size: 1.1rem; /* Slightly larger */
  padding: 10px 14px; /* Better clickable area */
  transition: all 0.3s ease-in-out;
  border-radius: 6px;
}

.navbar a:hover {
  background: rgba(255, 165, 0, 0.2);
  color: #ffa500;
}

/* Responsive */
@media (max-width: 768px) {
  .navbar ul {
    flex-direction: column;
    gap: 14px;
  }

  .navbar {
    padding: 1rem;
  }

  .navbar .logo {
    font-size: 1.6rem; /* Slightly smaller for mobile */
  }

  .navbar a {
    font-size: 1rem; /* Adjusted for smaller screens */
  }
}

</style>

