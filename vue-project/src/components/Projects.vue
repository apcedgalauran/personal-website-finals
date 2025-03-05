<template>
  <section class="projects">
    <h2>Projects</h2>
    <div class="grid">
      <div v-for="project in projects" :key="project.id" class="project-card">
        <img :src="project.image" :alt="project.title" />
        <h3>{{ project.title }}</h3>
        <p>{{ project.description }}</p>
        <a :href="project.link" class="btn">View Project</a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
const projects = ref([
  { id: 1, title: "Portfolio Website", description: "Vue.js + Tailwind", link: "#", image: "/project1.jpg" },
  { id: 2, title: "E-commerce Store", description: "Vue.js + Firebase", link: "#", image: "/project2.jpg" }
]);
</script>

<style scoped>
.projects {
  text-align: center;
  padding: 2rem;
}

.project-card {
  background: white;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
}

.project-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.project-card img {
  width: 100%;
  border-radius: 5px;
}
</style>
