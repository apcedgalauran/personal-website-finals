<template>
    <div>
      <!-- Hero Section -->
      <section id="home" class="hero">
        <div class="content">
          <h1>Hi, I'm <span class="highlight">Ezekiel Galauran</span></h1>
          <p>I'm a second-year CS student at Asia Pacific College, passionate about software and systems development. I have a deep interest in technology and enjoy solving problems.</p>
          <a href="#about" class="btn">Learn More</a>
        </div>
        <div class="image-frame">
          <img src=".assets/_MG_0603.JPG" alt="Your Picture">
        </div>
      </section>
  
      <!-- About Section -->
      <section id="about" class="about">
        <div class="content">
          <h2>About Me</h2>
          <p>I'm a second-year Computer Science student at Asia Pacific College. I was previously a national champion in journalism during my secondary studies at Las Piñas City National Science High School.</p>
          <p>I’m passionate about learning new programming languages and technologies. In my college journey, I've explored Java and Python, and I'm always excited to improve my skills.</p>
  
          <h3>My Hobbies</h3>
          <ul>
            <li>Playing the guitar</li>
            <li>Playing sports like basketball and volleyball</li>
            <li>Playing online games like Valorant</li>
          </ul>
  
          <h3>My Goal</h3>
          <p>My goal is to achieve financial freedom and make a positive impact through technology.</p>
  
          <h3>Favorite Video</h3>
          <p><a href="https://youtu.be/dQw4w9WgXcQ" target="_blank" class="favorite-video-link">Here is my favorite video of all time!</a></p>
        </div>
      </section>
  
      <!-- Gallery Section -->
      <section id="gallery" class="gallery">
        <h3>Picture Gallery</h3>
        <div class="gallery-container">
          <div v-for="image in images" :key="image.src" class="gallery-item">
            <img :src="image.src" :alt="image.alt">
          </div>
        </div>
      </section>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const images = ref([
    { src: 'gallery1.jpg', alt: 'Gallery Image 1' },
    { src: 'gallery2.jpg', alt: 'Gallery Image 2' },
    { src: 'gallery3.jpg', alt: 'Gallery Image 3' }
  ]);
  </script>
  
  <style scoped>
  .hero {
    display: flex;
    align-items: center;
    justify-content: space-around;
    padding: 50px;
  }
  
  .image-frame img {
    max-width: 200px;
    border-radius: 50%;
  }
  
  .gallery-container {
    display: flex;
    gap: 10px;
  }
  
  .gallery-item img {
    width: 100px;
    height: auto;
    border-radius: 5px;
  }
  </style>