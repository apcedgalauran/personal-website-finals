<template>
  <div>
    <!-- Hero Section -->
    <section ref="sections" id="home" class="hero">
      <div class="content slide-in-from-top">
        <h1>Hi, I'm <span class="highlight">Ezekiel Galauran</span></h1>
        <p>I'm a second-year CS student at Asia Pacific College, passionate about software and systems development. I have a deep interest in technology and enjoy solving problems.</p>
        <a href="#about" class="btn">Learn More</a>
      </div>
      <div class="image-frame slide-in-from-left">
        <img :src="image" alt="Profile Image" />
      </div>
    </section>
    
    <!-- About Section -->
    <section ref="sections" id="about" class="about slide-in-from-top">
      <div class="content">
        <h2>About Me</h2>
        <p>I'm a second-year Computer Science student at Asia Pacific College. I was previously a national champion in journalism during my secondary studies at Las Piñas City National Science High School.</p>
        <p>I’m passionate about learning new programming languages and technologies. In my college journey, I've explored Java and Python, and I'm always excited to improve my skills.</p>

        <h3>My Hobbies</h3>
        <div class="hobbies">
          <div class="hobby-card">
            <i class="hobby-icon fas fa-guitar"></i>
            <p>Playing different instruments like guitar, piano, drums, and exploring different genres of music.</p>
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

    <!-- Gallery Section -->
    <section ref="sections" id="gallery" class="gallery slide-in-from-top">
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
  </div>
</template>


<script setup>
import { ref, onMounted } from "vue";

// Store section elements and scroll direction
const sectionRefs = ref([]);
const isScrollingDown = ref(false);
const isModalOpen = ref(false);
const selectedImage = ref(null);
const galleryImages = ref(["eze1.jpg", "eze2.jfif", "eze3.jpg", "eze4.jpg"]);

const getImageUrl = (fileName) => {
  return new URL(`../assets/${fileName}`, import.meta.url).href;
};

const openModal = (img) => {
  selectedImage.value = img;
  isModalOpen.value = true;
};

const closeModal = () => {
  isModalOpen.value = false;
};

const image = new URL('@/assets/_MG_0603.JPG', import.meta.url).href;

onMounted(() => {
  // Cascading wave animation: left content first, then image
  const contentElement = document.querySelector(".hero .content");
  const imageElement = document.querySelector(".hero .image-frame");

  if (contentElement) {
    contentElement.style.setProperty('animation', 'waveSlideDown 1.2s cubic-bezier(0.34, 1.56, 0.64, 1) forwards', 'important');
  }
  
  if (imageElement) {
    imageElement.style.setProperty('animation', 'waveSlideDown 1.2s cubic-bezier(0.34, 1.56, 0.64, 1) 0.4s forwards', 'important');
  }

  // Set up Intersection Observer for about and gallery sections
  const observerOptions = {
    root: null,
    rootMargin: '-100px 0px -100px 0px',
    threshold: 0.2
  };

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('animate-in');
        observer.unobserve(entry.target);
      }
    });
  }, observerOptions);

  // Observe about and gallery sections
  const aboutSection = document.getElementById('about');
  const gallerySection = document.getElementById('gallery');
  
  if (aboutSection) observer.observe(aboutSection);
  if (gallerySection) observer.observe(gallerySection);
});
</script>


<style scoped>/* Slide-in effect from top */
/* Slide-in effect */
/* Hero Section */
.hero {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 80px 10%;
  gap: 40px;
  text-align: left;
  min-height: 100vh;
  background-color: var(--color-bg-primary, #FFFFFF);
  flex-wrap: wrap;
  width: 100%;
  box-sizing: border-box;
  opacity: 1; /* Hero container visible, children animated */
}

/* Ensures text stays readable */
.content {
  max-width: 700px;
  flex: 1;
  min-width: 300px;
}

/* Hero specific content animation */
.hero .content {
  opacity: 0;
  animation: waveSlideDown 1.2s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
}

/* Text Styling */
.hero h1 {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 15px;
  color: var(--color-text-primary, #4A3F35);
}

.hero .highlight {
  color: var(--color-accent-secondary, #B8956A);
}

.hero p {
  font-size: 1.2rem;
  margin-bottom: 30px;
  color: var(--color-text-secondary, #6B5D52);
}

/* Button */
.btn {
  display: inline-block;
  padding: 12px 28px;
  font-size: 1.1rem;
  font-weight: bold;
  color: var(--color-bg-primary, #FFFFFF);
  background-color: var(--color-accent-primary, #D4A574);
  border-radius: var(--radius-sm, 8px);
  text-decoration: none;
  transition: all var(--transition-base, 0.3s ease);
}

.btn:hover {
  background-color: var(--color-accent-secondary, #B8956A);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px var(--color-shadow-hover, rgba(74, 63, 53, 0.15));
}

/* Profile Picture Styling */
.image-frame {
  flex-shrink: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 35vw;
  max-width: 400px;
  height: auto;
  aspect-ratio: 1 / 1;
  overflow: hidden;
  border-radius: 50%;
}

/* Hero specific image animation */
.hero .image-frame {
  opacity: 0;
  animation: waveSlideDown 1.2s cubic-bezier(0.34, 1.56, 0.64, 1) 0.4s forwards;
}

.image-frame img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
}

@keyframes slideIn {
  0% {
    opacity: 0;
    transform: translateY(-100px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Smooth wave cascading animation */
@keyframes waveSlideDown {
  0% {
    opacity: 0;
    transform: translateY(-80px) translateX(-20px) scale(0.95);
  }
  60% {
    transform: translateY(10px) translateX(0) scale(1.02);
  }
  100% {
    opacity: 1;
    transform: translateY(0) translateX(0) scale(1);
  }
}

@keyframes slideInDown {
  0% {
    opacity: 0;
    transform: translateY(100px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideInUp {
  0% {
    opacity: 0;
    transform: translateY(-100px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

.about {
  opacity: 0;
  transform: translateY(50px);
}

.about.animate-in {
  animation: slideInUp 1s ease-out forwards;
}

.gallery {
  opacity: 0;
  transform: translateY(50px);
}

.gallery.animate-in {
  animation: slideInUp 1s ease-out forwards;
}

.gallery .gallery-item {
  opacity: 1;
}

/* Navigation Styling */
nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #333;
  color: white;
  padding: 10px;
  z-index: 1000;
}

nav ul {
  display: flex;
  justify-content: space-around;
  list-style-type: none;
}

nav a {
  color: white;
  text-decoration: none;
  padding: 10px;
  transition: 0.3s;
}

nav a:hover {
  background-color: var(--color-bg-tertiary, #F5F1ED);
}
/* General Layout */
body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
  margin: 0;
  padding: 0;
  overflow-x: hidden; /* Prevents horizontal scrolling */
}


/* About Section */
.section {
  text-align: center; /* Centers all inline content */
  padding: 40px 20px;
  background-color: var(--color-bg-secondary, #FAF8F5);
}

.section h4 {
  font-size: 20px;
  margin-bottom: 20px;
  color: var(--color-text-primary, #4A3F35);
  text-align: center; /* Ensures the heading itself is centered */
  width: 100%; /* Ensures it spans the full width */
  display: block; /* Makes sure it behaves as a block element */
}

.about {
  padding: 60px 10%;
  background: var(--color-bg-secondary, #FAF8F5);
  text-align: left;
  width: 100%;
  box-sizing: border-box;
  box-shadow: 0px 2px 12px var(--color-shadow, rgba(74, 63, 53, 0.08));
}

.about .content {
  max-width: 800px;
  margin: 0 auto;
  opacity: 1;
}

.about h2,
.about h3 {
  color: var(--color-text-primary, #4A3F35);
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
  background-color: var(--color-accent-primary, #D4A574);
  position: absolute;
  bottom: 0;
  left: 0;
}

.about p {
  font-size: 1.1rem;
  color: var(--color-text-secondary, #6B5D52);
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
  background-color: var(--color-bg-card, #FDFCFB);
  padding: 16px;
  border-radius: var(--radius-md, 12px);
  flex: 1 1 250px;
  display: flex;
  align-items: center;
  gap: 12px;
  transition: all var(--transition-base, 0.3s ease);
  font-size: 1.1rem;
  color: var(--color-text-primary, #4A3F35);
  font-weight: 500;
  border: 1px solid var(--color-border, #E8E3DD);
  box-shadow: 0 2px 8px var(--color-shadow, rgba(74, 63, 53, 0.08));
}

.hobby-card:hover {
  background-color: var(--color-bg-tertiary, #F5F1ED);
  transform: translateY(-5px);
  box-shadow: 0 4px 16px var(--color-shadow-hover, rgba(74, 63, 53, 0.15));
}

.hobby-icon {
  font-size: 1.8rem;
  color: var(--color-accent-secondary, #B8956A);
}
/* Goal & Video Sections */
.goal-card, .video-card {
  background-color: var(--color-bg-card, #FDFCFB);
  padding: 16px;
  border-radius: var(--radius-md, 12px);
  display: flex;
  align-items: center;
  gap: 12px;
  transition: all var(--transition-base, 0.3s ease);
  font-size: 1.1rem;
  color: var(--color-text-primary, #4A3F35);
  font-weight: 500;
  border: 1px solid var(--color-border, #E8E3DD);
  box-shadow: 0 2px 8px var(--color-shadow, rgba(74, 63, 53, 0.08));
  margin-top: 10px;
}

.goal-card:hover, .video-card:hover {
  background-color: var(--color-bg-tertiary, #F5F1ED);
  transform: translateY(-5px);
  box-shadow: 0 4px 16px var(--color-shadow-hover, rgba(74, 63, 53, 0.15));
}

.goal-icon, .video-icon {
  font-size: 1.8rem;
  color: var(--color-accent-secondary, #B8956A);
}

/* Favorite Video Link */
.favorite-video-link {
  font-weight: bold;
  color: var(--color-accent-secondary, #B8956A);
  text-decoration: none;
  transition: color var(--transition-base, 0.3s ease);
}

.favorite-video-link:hover {
  color: var(--color-accent-hover, #9D7F57);
  text-decoration: underline;
}
/* Gallery Section */
.gallery {
  text-align: center;
  padding: 60px 20px;
  background-color: var(--color-bg-primary, #FFFFFF);
}

.gallery h4 {
  font-size: 28px;
  font-weight: bold;
  margin-bottom: 25px;
  color: var(--color-text-primary, #4A3F35);
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
  border-radius: var(--radius-md, 12px);
  cursor: pointer;
  transition: transform var(--transition-base, 0.3s ease), box-shadow var(--transition-base, 0.3s ease);
  border: 2px solid var(--color-border, #E8E3DD);
}

/* Make the last image centered at the bottom */
.gallery-item:last-child {
  grid-column: 2 / 3; /* Places it in the center column */
}

/* Hover Effect */
.gallery-item img:hover {
  transform: scale(1.05);
  box-shadow: 0px 6px 16px var(--color-shadow-hover, rgba(74, 63, 53, 0.15));
}

/* Modal Styles */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(74, 63, 53, 0.9);
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
  border-radius: var(--radius-md, 12px);
  box-shadow: 0px 8px 24px rgba(74, 63, 53, 0.3);
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
    padding-top: 150px;
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