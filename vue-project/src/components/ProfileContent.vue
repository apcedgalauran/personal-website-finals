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
          <img :src="image" alt="Profile Image" />
        </div> 
      </section> <!-- ✅ Correctly closing the section -->
    </div>
      <!-- About Section -->
<section id="about" class="about">
  <div class="content">
    <h2>About Me</h2>
    <p>I'm a second-year Computer Science student at Asia Pacific College. I was previously a national champion in journalism during my secondary studies at Las Piñas City National Science High School.</p>
    <p>I’m passionate about learning new programming languages and technologies. In my college journey, I've explored Java and Python, and I'm always excited to improve my skills.</p>

    <h3>My Hobbies</h3>
    <div class="hobbies">
      <div class="hobby-card">
        <i class="hobby-icon fas fa-guitar"></i>
        <p>Playing different instruments like guitar, piano, drums and exploring different genres of music.</p>
      </div>
      <div class="hobby-card">
        <i class="hobby-icon fas fa-basketball-ball"></i>
        <p>Enjoying basketball and volleyball games, whether for fun or competition.</p>
      </div>
      <div class="hobby-card">
        <i class="hobby-icon fas fa-gamepad"></i>
        <p>Immersing myself in online games like Valorant to unwind and challenge my reflexes.</p>
      </div>
    </div>  

    <h3>My Goal</h3>
    <div class="goal-card">
      <i class="goal-icon fas fa-bullseye"></i>
      <p>My ambition is to achieve financial freedom while using technology to create meaningful and lasting impacts in the world.</p>
    </div>

    <h3>Favorite Video</h3>
    <div class="video-card">
      <i class="video-icon fas fa-video"></i>
      <p>There's one video that always lifts my mood. <a href="https://youtu.be/dQw4w9WgXcQ" target="_blank" class="favorite-video-link">Check it out here!</a></p>
    </div>

  </div>
</section>

<section id = "gallery" class="gallery">
    <h4>Picture Gallery</h4>
    <div class="gallery-grid">
      <div v-for="(img, index) in galleryImages" :key="index" class="gallery-item">
        <img :src="getImageUrl(img)" alt="Gallery Image" @click="openModal(img)" />
      </div>
    </div>

    <!-- Image Modal -->
    <div v-if="isModalOpen" class="modal" @click="closeModal">
      <div class="modal-content">
        <img :src="getImageUrl(selectedImage)" alt="Full Image" />
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";


const galleryImages = ref(["eze1.jpg", "eze2.jfif", "eze3.jpg", "eze4.jpg"]);
const selectedImage = ref(null);
const isModalOpen = ref(false);

const getImageUrl = (fileName) => {
  return new URL(`../assets/${fileName}`, import.meta.url).href;
};

// Open modal with selected image
const openModal = (img) => {
  selectedImage.value = img;
  isModalOpen.value = true;
};

// Close modal


const closeModal = () => {
  isModalOpen.value = false;
};


  const image = new URL('@/assets/_MG_0603.JPG', import.meta.url).href;

  </script>
  
  <style scoped>
/* General Layout */
body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
  margin: 0;
  padding: 0;
  overflow-x: hidden; /* Prevents horizontal scrolling */
}

/* Hero Section */
.hero {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 80px 10%;
  gap: 40px;
  text-align: left;
  min-height: 100vh; /* Increased from 90vh to 100vh to take up the full height of the screen */
  background-color: #0d0d0d;
  flex-wrap: wrap; /* Allows elements to stack on smaller screens */
  width: 100%;
  box-sizing: border-box;
}

/* Ensures text stays readable */
.content {
  max-width: 700px;
  flex: 1;
  min-width: 300px; /* Prevents text from getting too narrow */
}

/* Text Styling */
.hero h1 {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 15px;
  color: #ffffff;
}

.hero p {
  font-size: 1.2rem;
  margin-bottom: 30px;
  color: #e0e0e0;
}

/* Button */
.btn {
  display: inline-block;
  padding: 12px 28px;
  font-size: 1.1rem;
  font-weight: bold;
  color: #fff;
  background-color: #e68a00;
  border-radius: 8px;
  text-decoration: none;
  transition: all 0.3s ease-in-out;
}

.btn:hover {
  background-color: #cc7700;
  transform: scale(1.05);
}

/* Profile Picture Styling */
.image-frame {
  flex-shrink: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 35vw; /* Slightly smaller for better spacing */
  max-width: 400px;
  height: auto;
  aspect-ratio: 1 / 1;
  overflow: hidden;
  border-radius: 50%;
}

.image-frame img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
}

/* About Section */
.section {
  text-align: center; /* Centers all inline content */
  padding: 40px 20px;
  background-color: #f8f9fa;
}

.section h4 {
  font-size: 20px;
  margin-bottom: 20px;
  color: #333;
  text-align: center; /* Ensures the heading itself is centered */
  width: 100%; /* Ensures it spans the full width */
  display: block; /* Makes sure it behaves as a block element */
}

.about {
  padding: 60px 10%;
  background: linear-gradient(135deg, #1a1a1a, #292929);
  text-align: left;
  width: 100%;
  box-sizing: border-box;
  border-radius: 10px;
  box-shadow: 0px 4px 20px rgba(0, 0, 0, 0.4);
}

.about .content {
  max-width: 800px;
  margin: 0 auto;
}

.about h2,
.about h3 {
  color: #f8f9fa;
  position: relative;
  display: inline-block;
  padding-bottom: 8px;
}

.about h2::after,
.about h3::after {
  content: "";
  display: block;
  width: 50px;
  height: 3px;
  background-color: #e68a00;
  position: absolute;
  bottom: 0;
  left: 0;
}

.about p {
  font-size: 1.1rem;
  color: #d1d1d1;
  line-height: 1.6;
}

/* Hobbies Section */
.hobbies {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  margin-top: 20px;
}

.hobby-card {
  background-color: rgba(255, 255, 255, 0.05);
  padding: 16px;
  border-radius: 10px;
  flex: 1 1 250px;
  display: flex;
  align-items: center;
  gap: 12px;
  transition: all 0.3s ease-in-out;
  font-size: 1.1rem;
  color: #f8f9fa;
  font-weight: 500;
  box-shadow: 0 4px 10px rgba(255, 136, 0, 0.2);
}

.hobby-card:hover {
  background-color: rgba(255, 136, 0, 0.2);
  transform: translateY(-5px);
}

.hobby-icon {
  font-size: 1.8rem;
  color: #e68a00;
}
/* Goal & Video Sections */
.goal-card, .video-card {
  background-color: rgba(255, 255, 255, 0.05);
  padding: 16px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  gap: 12px;
  transition: all 0.3s ease-in-out;
  font-size: 1.1rem;
  color: #f8f9fa;
  font-weight: 500;
  box-shadow: 0 4px 10px rgba(255, 136, 0, 0.2);
  margin-top: 10px;
}

.goal-card:hover, .video-card:hover {
  background-color: rgba(255, 136, 0, 0.2);
  transform: translateY(-5px);
}

.goal-icon, .video-icon {
  font-size: 1.8rem;
  color: #e68a00;
}

/* Favorite Video Link */
.favorite-video-link {
  font-weight: bold;
  color: #e68a00;
  text-decoration: none;
  transition: color 0.3s ease-in-out;
}

.favorite-video-link:hover {
  color: #ff9800;
  text-decoration: underline;
}


.favorite-video-link:hover {
  color: #ff9800;
  text-decoration: underline;
}
/* Gallery Section */
.gallery {
  text-align: center;
  padding: 60px 20px;
  background-color: #0d0d0d;
  border-radius: 12px;
}

.gallery h4 {
  font-size: 28px;
  font-weight: bold;
  margin-bottom: 25px;
  color: #f7f7f7;
  letter-spacing: 1px;
}

/* Grid Layout */
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 columns by default */
  gap: 20px;
  max-width: 1000px;
  margin: auto;
  padding: 20px;
}

/* Responsive Gallery Layout */
@media (max-width: 768px) { 
  .gallery-grid { 
    grid-template-columns: repeat(2, 1fr); /* 2 columns on smaller screens */ 
  } 
}

@media (max-width: 480px) { 
  .gallery-grid { 
    grid-template-columns: repeat(1, 1fr); /* 1 column for very small screens */ 
  } 
}

/* Image Styling - Uniform Size */
.gallery-item img {
  width: 100%;
  height: 250px;
  object-fit: cover;
  border-radius: 12px;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  border: 3px solid rgba(0, 0, 0, 0.1);
}

/* Make the last image centered at the bottom */
.gallery-item:last-child {
  grid-column: 2 / 3; /* Places it in the center column */
}

/* Hover Effect */
.gallery-item img:hover {
  transform: scale(1.05);
  box-shadow: 0px 6px 12px rgba(0, 0, 0, 0.2);
}

/* Modal Styles */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  animation: fadeIn 0.3s ease-in-out;
}

/* Modal Content */
.modal-content {
  max-width: 80%;
  max-height: 80%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal img {
  width: auto;
  height: auto;
  max-width: 100%;
  max-height: 90vh;
  border-radius: 10px;
  box-shadow: 0px 8px 16px rgba(255, 255, 255, 0.2);
}

/* Fade-in animation */
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

/* RESPONSIVE BREAKPOINTS */

/* Ensure Navbar Doesn't Overlap Hero */
@media (max-width: 1024px) {
  .hero {
    flex-direction: column-reverse; /* Image below text */
    text-align: center;
    padding: 120px 5% 60px; /* Extra padding at top */
    min-height: auto;
  }

  .image-frame {
    width: 45vw;
    max-width: 350px;
  }

  .hero h1 {
    font-size: 2.5rem;
  }

  .hero p {
    font-size: 1.1rem;
  }
}

@media (max-width: 768px) {
  .hero {
    flex-direction: column-reverse;
    text-align: center;
    padding: 100px 5% 50px; /* Extra padding to push below navbar */
    gap: 20px;
  }

  .image-frame {
    width: 60vw;
    max-width: 300px;
  }

  .hero h1 {
    font-size: 2rem;
  }

  .hero p {
    font-size: 1rem;
  }

  .btn {
    padding: 10px 24px;
    font-size: 1rem;
  }
}

</style>