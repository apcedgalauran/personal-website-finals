<template>
  <section id="guestbook" class="guestbook">
    <h2>Guestbook</h2>
    <form @submit.prevent="addMessage">
      <input v-model="name" placeholder="Your Name" required />
      <input v-model="email" type="email" placeholder="Your Email" required />
      <textarea v-model="message" placeholder="Leave a message..." required></textarea>
      <button class="btn" type="submit" :disabled="loading">Submit</button>
    </form>
    <ul>
      <li v-for="entry in messages" :key="entry.id">
        <strong>{{ entry.name }}</strong> ({{ entry.email }}) - 
        {{ new Date(entry.created_at).toLocaleString() }}:
        <p>{{ entry.message }}</p>
      </li>
    </ul>
  </section>
</template>

<script>
import { supabase } from '@/lib/supabaseClient';


export default {
  data() {
    return {
      name: '',
      email: '',
      message: '',
      messages: [],
      loading: false,
    };
  },
  async created() {
  await this.fetchMessages();

  // Listen for new messages in real-time
  supabase
    .channel('guestbook')
    .on('postgres_changes', { event: 'INSERT', schema: 'public', table: 'guestbook' }, (payload) => {
      this.messages.unshift(payload.new);
    })
    .subscribe();
  },
  methods: {
    async fetchMessages() {
      let { data, error } = await supabase.from('guestbook').select('*').order('created_at', { ascending: false });
      if (!error) {
        this.messages = data;
      }
    },
    async addMessage() {
  if (!this.name || !this.email || !this.message) return;
  this.loading = true;

  const { error } = await supabase.from('guestbook').insert([
    { name: this.name, email: this.email, message: this.message, created_at: new Date().toISOString() },
  ]);

  if (!error) {
    await this.fetchMessages(); // Re-fetch messages after insert
    this.name = '';
    this.email = '';
    this.message = '';
  }

  this.loading = false;
    },
  },
};
</script>

<style scoped>
.guestbook {
  text-align: center;
  padding: 2rem;
  background-color: #f2f2f2; /* Light grey background */
  border-radius: 10px; /* Optional: Adds a rounded border for a smooth look */
}

form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 500px;
  margin: auto;
}

input, textarea {
  padding: 10px;
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 1rem;
}

textarea {
  height: 100px;
}

button {
  background: var(--primary-color, #c37d0f);
  color: white;
  padding: 10px;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.3s ease-in-out;
}

button:hover {
  background: #a6670d;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

li {
  background: #2b2b2b;
  color: white;
  padding: 10px;
  border-radius: 5px;
  margin-bottom: 10px;
  text-align: left;
}

</style>