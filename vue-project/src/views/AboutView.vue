<template>
  <div class="about">
    <h1>About Me</h1>
    <p class="description">
      I'm a <strong>[Your Field/Profession]</strong> with a passion for coding, music, and adventure. 
      Currently learning Vue.js and working with Supabase.
    </p>

    <div class="info-cards">
      <div class="card">
        <h2>🎸 Music</h2>
        <p>I play the guitar and piano, and I love composing music.</p>
      </div>
      <div class="card">
        <h2>🏍️ Motorcycle Rides</h2>
        <p>I enjoy riding through scenic routes and exploring new places.</p>
      </div>
      <div class="card">
        <h2>💻 Coding</h2>
        <p>Building web apps using Vue.js, JavaScript, and Supabase.</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.about {
  max-width: 800px;
  margin: auto;
  padding: 50px;
  text-align: center;
  background: #f8fafc;
  color: #1e293b;
}

.description {
  font-size: 1.2rem;
  margin-bottom: 30px;
  opacity: 0.8;
}

.info-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.card {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease-in-out;
}

.card:hover {
  transform: translateY(-5px);
}
</style>
