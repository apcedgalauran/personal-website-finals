<template>
  <div :class="theme">
    <nav>
      <h1>My Portfolio</h1>
      <button @click="toggleTheme">
        <span v-if="theme === 'light'">🌙 Dark Mode</span>
        <span v-else>☀️ Light Mode</span>
      </button>
    </nav>
    <router-view />
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const theme = ref(localStorage.getItem("theme") || "light");

const toggleTheme = () => {
  theme.value = theme.value === "light" ? "dark" : "light";
  localStorage.setItem("theme", theme.value);
};

// Apply saved theme on load
onMounted(() => {
  document.body.classList.add(theme.value);
});
</script>

<style scoped>
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  background: var(--nav-bg);
  color: var(--text-color);
}

button {
  padding: 8px 15px;
  border: none;
  background: var(--btn-bg);
  color: var(--btn-text);
  cursor: pointer;
  border-radius: 5px;
  transition: 0.3s;
}

button:hover {
  background: var(--btn-hover);
}
</style>
