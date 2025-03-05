<template>
  <div class="home">
    <div class="content">
      <img src="../assets/_MG_0603.JPG" alt="Profile Picture" class="profile-img" />
      <h1>Hello, I'm <span class="highlight">Ezekiel Galauran</span></h1>
      <p class="intro">
         I enjoy coding, music, and motorcycle rides.
      </p>
      <router-link to="/about" class="cta-button">Learn More About Me</router-link>
    </div>
  </div>
</template>

<style scoped>
.home {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  text-align: center;
  background: linear-gradient(135deg, #1e293b, #0f172a);
  color: white;
}

.content {
  max-width: 600px;
  padding: 30px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 15px;
  backdrop-filter: blur(10px);
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
}

.profile-img {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  border: 3px solid #facc15;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s ease-in-out;
}

.profile-img:hover {
  transform: scale(1.1);
}

h1 {
  margin-top: 15px;
  font-size: 2rem;
  font-weight: bold;
}

.highlight {
  color: #facc15;
}

.intro {
  font-size: 1.1rem;
  margin-top: 10px;
  opacity: 0.9;
}

.cta-button {
  display: inline-block;
  margin-top: 20px;
  padding: 10px 20px;
  font-size: 1rem;
  font-weight: bold;
  background: #facc15;
  color: #1e293b;
  border-radius: 5px;
  text-decoration: none;
  transition: background 0.3s;
}

.cta-button:hover {
  background: #eab308;
}
</style>
