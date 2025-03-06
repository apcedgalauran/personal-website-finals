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
          <img src="./assets/_MG_0603.JPG" alt="Your Picture">
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

      <!-- Footer -->
      <footer class="footer">
        <p>Asia Pacific College</p>
      </footer>
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
  /* General Layout */
  body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
  }
  
/* Hero Section */
.hero {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 100px 15%;
  gap: 50px;
  text-align: left;
  min-height: 90vh;
  background-color: #0d0d0d;
}

.content {
  max-width: 700px;
}

.hero h1 {
  font-size: 3.5rem;
  font-weight: bold;
  margin-bottom: 15px;
  color: #ffffff;
}

.hero p {
  font-size: 1.3rem;
  margin-bottom: 40px;
  color: #e0e0e0;
}

/* Improved Button */
.btn {
  display: inline-block;
  padding: 14px 30px;
  font-size: 1.2rem;
  font-weight: bold;
  color: #fff;
  background-color: #e68a00;
  border: none;
  border-radius: 8px;
  text-decoration: none;
  transition: all 0.3s ease-in-out;
  box-shadow: 0 4px 12px rgba(255, 165, 0, 0.3);
}

.btn:hover {
  background-color: #cc7700;
  transform: scale(1.1);
  box-shadow: 0 6px 18px rgba(255, 165, 0, 0.4);
}

/* About Section */
.about {
  padding: 60px 10%;
  background-color: #121212;
  text-align: left;
}

.about .content {
  max-width: 800px;
  margin: 0 auto;
}

.about h2 {
  font-size: 2rem;
  font-weight: bold;
  margin-bottom: 20px;
  color: #f8f9fa; /* Improved contrast */
}

.about h3 {
  font-size: 1.5rem;
  margin-top: 20px;
  color: #e0e0e0; /* Improved contrast */
}

.about p {
  font-size: 1.1rem;
  line-height: 1.6;
  color: #d1d1d1; /* Improved contrast */
  margin-bottom: 15px;
}

.about ul {
  list-style-type: disc;
  padding-left: 20px;
}

.about ul li {
  font-size: 1.1rem;
  margin-bottom: 10px;
  color: #c0c0c0; /* Improved contrast */
}

/* Gallery Section */
.gallery {
  padding: 60px 10%;
  background-color: #1a1a1a;
  text-align: center;
}

.gallery h3 {
  font-size: 2rem;
  font-weight: bold;
  margin-bottom: 20px;
  color: #ffffff;
}

.gallery-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  justify-content: center;
  align-items: center;
}

.gallery-item {
  overflow: hidden;
  border-radius: 10px;
  transition: transform 0.3s ease-in-out;
}

.gallery-item img {
  width: 100%;
  height: auto;
  border-radius: 10px;
  object-fit: cover;
  transition: transform 0.3s ease-in-out;
}

.gallery-item:hover {
  transform: scale(1.05);
}

.gallery-item img:hover {
  transform: scale(1.1);
}

  /* Image Styling */
  .image-frame {
    flex-shrink: 0;
    display: flex;
    justify-content: center;
  }

  .footer {
  background: #1e1e1e;
  color: #f0f0f0;
  text-align: center;
  padding: 1rem;
  font-size: 1rem;
  font-weight: bold;
  position: relative;
  bottom: 0;
  width: 100%;
  box-shadow: 0 -4px 10px rgba(0, 0, 0, 0.2);
}

.footer p {
  margin: 0;
  transition: color 0.3s ease-in-out;
}

.footer p:hover {
  color: #ffa500;
}

</style>