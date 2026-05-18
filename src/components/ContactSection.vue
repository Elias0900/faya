<template>
  <section id="contact" class="contact-section">
    <div class="container">
      <div class="contact-wrapper reveal">
        <div class="contact-info reveal-left">
          <span class="section-tag">Contact</span>
          <h2 class="contact-title">Prêt à passer<br /><span class="gold-gradient">au niveau supérieur ?</span></h2>
          <p class="contact-desc">
            Envoie-moi un message et je te réponds sous 24h pour organiser
            une première séance d'essai gratuite.
          </p>
          <div class="contact-perks">
            <div class="perk" v-for="p in perks" :key="p.text">
              <div class="perk-icon">{{ p.icon }}</div>
              <div class="perk-text">{{ p.text }}</div>
            </div>
          </div>
        </div>

        <form class="contact-form reveal-right" @submit.prevent="handleSubmit">
          <div class="form-row">
            <div class="field">
              <label>Prénom</label>
              <input type="text" v-model="form.name" placeholder="Thomas" required />
            </div>
            <div class="field">
              <label>Email</label>
              <input type="email" v-model="form.email" placeholder="thomas@email.com" required />
            </div>
          </div>
          <div class="field">
            <label>Niveau actuel</label>
            <select v-model="form.level">
              <option value="">Sélectionne ton niveau</option>
              <option>Débutant (jamais joué)</option>
              <option>Loisir (quelques années)</option>
              <option>Compétition (club)</option>
              <option>Semi-pro / Pro</option>
            </select>
          </div>
          <div class="field">
            <label>Message</label>
            <textarea v-model="form.message" rows="4" placeholder="Tes objectifs, disponibilités..."></textarea>
          </div>
          <button type="submit" class="submit-btn" :class="{ sent }">
            <span v-if="!sent">Envoyer ma demande →</span>
            <span v-else>✓ Message envoyé !</span>
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'

const sent = ref(false)
const form = reactive({ name: '', email: '', level: '', message: '' })

const perks = [
  { icon: '🎁', text: '1ère séance d\'essai offerte' },
  { icon: '⚡', text: 'Réponse sous 24h garantie' },
  { icon: '📍', text: 'Bretagne · En ligne disponible' },
]

function handleSubmit() {
  sent.value = true
  setTimeout(() => {
    sent.value = false
    Object.assign(form, { name: '', email: '', level: '', message: '' })
  }, 3000)
}
</script>

<style scoped>
.contact-section {
  padding: 100px 0 120px;
}
.contact-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: start;
}
.section-tag {
  display: inline-block;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 16px;
}
.contact-title {
  font-size: clamp(22px, 2.8vw, 36px);
  font-weight: 900;
  line-height: 1.1;
  letter-spacing: -1px;
  margin-bottom: 20px;
}
.gold-gradient {
  background: linear-gradient(135deg, var(--gold), var(--gold-light));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.contact-desc {
  color: var(--gray-light);
  font-size: 14px;
  line-height: 1.7;
  margin-bottom: 40px;
}
.contact-perks {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
.perk {
  display: flex;
  align-items: center;
  gap: 14px;
}
.perk-icon {
  width: 40px;
  height: 40px;
  background: var(--gold-dim);
  border: 1px solid rgba(192,154,48,0.2);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  flex-shrink: 0;
}
.perk-text {
  font-size: 14px;
  color: var(--gray-light);
  font-weight: 500;
}

/* Form */
.contact-form {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 40px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
.field {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
label {
  font-size: 13px;
  font-weight: 600;
  color: var(--gray-light);
  letter-spacing: 0.3px;
}
input, select, textarea {
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 12px 16px;
  color: var(--white);
  font-family: var(--font);
  font-size: 14px;
  outline: none;
  transition: border-color 0.3s;
  resize: vertical;
}
input::placeholder, textarea::placeholder {
  color: var(--gray-mid);
}
input:focus, select:focus, textarea:focus {
  border-color: var(--gold);
}
select option {
  background: var(--bg-card);
}
.submit-btn {
  background: var(--gold);
  color: #000;
  border: none;
  border-radius: 10px;
  padding: 16px;
  font-size: 14px;
  font-weight: 700;
  font-family: var(--font);
  cursor: pointer;
  transition: all 0.3s;
  box-shadow: 0 4px 20px rgba(192,154,48,0.3);
}
.submit-btn:hover:not(.sent) {
  background: var(--gold-light);
  transform: translateY(-2px);
  box-shadow: 0 8px 30px rgba(192,154,48,0.45);
}
.submit-btn.sent {
  background: #1a3a1a;
  color: #4ade80;
  box-shadow: none;
  cursor: default;
}

@media (max-width: 960px) {
  .contact-section { padding: 72px 0 96px; }
  .contact-wrapper { grid-template-columns: 1fr; gap: 48px; }
  .form-row { grid-template-columns: 1fr 1fr; }
  .contact-title { font-size: clamp(26px, 4vw, 36px); }
}
@media (max-width: 640px) {
  .contact-section { padding: 56px 0 80px; }
  .form-row { grid-template-columns: 1fr; }
  .contact-form { padding: 28px 20px; gap: 16px; }
  .contact-desc { font-size: 14px; }
}
</style>
