<template>
  <div>
    <!-- Navigation -->
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
      <router-link to="/guestbook">Guestbook</router-link>
    </nav>

    <!-- Dynamic Content -->
    <router-view></router-view>
  </div>
</template>

<style scoped>
nav {
  display: flex;
  gap: 20px;
  background: #333;
  padding: 10px;
}

nav a {
  color: white;
  text-decoration: none;
  font-weight: bold;
}

nav a:hover {
  text-decoration: underline;
}
</style>
