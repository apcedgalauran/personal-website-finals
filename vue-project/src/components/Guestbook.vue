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
      <transition-group name="fade" tag="ul">
        <li v-for="entry in messages" :key="entry.id">
          <strong>{{ entry.name }}</strong> ({{ entry.email }}) - 
          {{ new Date(entry.created_at).toLocaleString() }}:
          <p>{{ entry.message }}</p>
        </li>
      </transition-group>
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
        // Insert the new message at the top of the list with a smooth transition
        this.messages.unshift(payload.new);
      })
      .subscribe();
  },
  methods: {
    async fetchMessages() {
      let { data, error } = await supabase
        .from('guestbook')
        .select('*')
        .order('created_at', { ascending: false });
      if (!error) {
        this.messages = data;
      }
    },
    async addMessage() {
      if (!this.name || !this.email || !this.message) return;
      this.loading = true;

      // Insert the new message into the database
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
  padding: 3rem 2rem;
  background-color: var(--color-bg-secondary, #FAF8F5);
  border-radius: var(--radius-lg, 16px);
}

form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 500px;
  margin: auto;
}

input, textarea {
  padding: 12px;
  width: 100%;
  border: 2px solid var(--color-border, #E8E3DD);
  border-radius: var(--radius-sm, 8px);
  font-size: 1rem;
  background: var(--color-bg-primary, #FFFFFF);
  color: var(--color-text-primary, #4A3F35);
  transition: border-color var(--transition-base, 0.3s ease);
}

input:focus, textarea:focus {
  outline: none;
  border-color: var(--color-accent-secondary, #B8956A);
}

textarea {
  height: 100px;
}

button {
  background: var(--color-accent-primary, #D4A574);
  color: var(--color-bg-primary, #FFFFFF);
  padding: 12px 24px;
  border: none;
  border-radius: var(--radius-sm, 8px);
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all var(--transition-base, 0.3s ease);
}

button:hover {
  background: var(--color-accent-secondary, #B8956A);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px var(--color-shadow-hover, rgba(74, 63, 53, 0.15));
}

button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
  transform: none;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

/* Slide-in transition effect for the guestbook entries */
.slide-enter-active, .slide-leave-active {
  transition: transform 0.5s ease, opacity 0.5s ease;
}

.slide-enter, .slide-leave-to {
  transform: translateY(50px); /* Moves the element 50px down */
  opacity: 0; /* Makes the element invisible at the start and end of transition */
}

li {
  background: var(--color-bg-card, #FDFCFB);
  color: var(--color-text-primary, #4A3F35);
  padding: 16px;
  border-radius: var(--radius-md, 12px);
  margin-bottom: 12px;
  text-align: left;
  border: 1px solid var(--color-border-light, #F0EBE5);
  box-shadow: 0 2px 8px var(--color-shadow, rgba(74, 63, 53, 0.08));
}

li strong {
  color: var(--color-accent-secondary, #B8956A);
}

li p {
  color: var(--color-text-secondary, #6B5D52);
  margin-top: 8px;
}
</style>

