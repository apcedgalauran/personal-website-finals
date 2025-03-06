<template>
  <section id = "guestbook" class="section">
    <h2>Guestbook</h2>
    <form @submit.prevent="addMessage">
      <input v-model="name" placeholder="Your Name" required />
      <textarea v-model="message" placeholder="Leave a message..." required></textarea>
      <button class="btn" type="submit">Submit</button>
    </form>
    <ul>
      <li v-for="entry in messages" :key="entry.id">
        <strong>{{ entry.name }}</strong>: {{ entry.message }}
      </li>
    </ul>
  </section>
</template>

<style scoped>
.guestbook {
  text-align: center;
  padding: 2rem;
}

form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

input, textarea {
  padding: 10px;
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 5px;
}

textarea {
  height: 100px;
}

button {
  background: var(--primary-color);
  color: white;
}

button:hover {
  background: #0056b3;
}
</style>
