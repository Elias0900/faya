<template>
  <section id="testimonials" class="testimonials-section">
    <div class="container">
      <div class="section-header reveal">
        <span class="section-tag">Témoignages</span>
        <h2 class="section-title">Ce que disent<br /><span class="gold-gradient">les coachs pros</span></h2>
      </div>

      <div class="testimonials-track">
        <article
          v-for="(t, i) in testimonials"
          :key="i"
          class="t-card reveal"
          :style="{ transitionDelay: `${i * 0.12}s` }"
        >
          <!-- Guillemet décoratif -->
          <span class="t-mark">"</span>

          <!-- Étoiles -->
          <div class="t-stars"><span v-for="s in 5" :key="s">★</span></div>

          <!-- Quote -->
          <p class="t-quote">{{ t.text }}</p>

          <!-- Footer : avatar + identité -->
          <div class="t-footer">
            <div
              class="t-avatar"
              :style="t.photo ? { backgroundImage: `url(${t.photo})` } : {}"
            >
              <span v-if="!t.photo">{{ t.initials }}</span>
            </div>
            <div class="t-author">
              <span class="author-name">{{ t.name }}</span>
              <span class="author-role">{{ t.role }}</span>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// Pour ajouter une photo : photo: '/testimonials/prenom-nom.jpg'
// (placez l'image dans public/testimonials/)
const testimonials = [
  {
    text: "Une approche du coaching vraiment moderne. Il maîtrise l'individualisation du travail comme peu de coaches que j'ai croisés en professionnel — technique, mental, vidéo. Tout y est.",
    name: 'Marc Fontaine',
    role: 'Head Coach Pro B · Tours TC',
    initials: 'MF',
    photo: null,
  },
  {
    text: "Ses joueurs arrivent en club avec un niveau au-dessus. Rare pour un coach indépendant.",
    name: 'David Niang',
    role: 'Assistant Coach · JL Bourg-en-Bresse',
    initials: 'DN',
    photo: null,
  },
  {
    text: "Rigueur, exigence, précision. Chaque séance a un objectif mesurable. C'est ce qui fait la différence entre progresser et stagner.",
    name: 'Léa Morin',
    role: 'Coach nationale · Équipe de France 3x3',
    initials: 'LM',
    photo: null,
  },
  {
    text: "J'ai collaboré avec lui sur des stages d'été. Sa capacité à faire progresser un joueur en peu de séances est impressionnante. Il a une vraie vision du développement à long terme, et ça se voit dans les résultats.",
    name: 'Sylvain Berger',
    role: 'Responsable formation · Bretagne Basketball',
    initials: 'SB',
    photo: null,
  },
]
</script>

<style scoped>
.testimonials-section {
  padding: 100px 0;
  overflow: hidden;
}
.section-header {
  text-align: center;
  margin-bottom: 64px;
}
.section-tag {
  display: inline-block;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 16px;
}
.section-title {
  font-size: clamp(24px, 3.2vw, 40px);
  font-weight: 800;
  line-height: 1.1;
  letter-spacing: -1px;
}
.gold-gradient {
  background: linear-gradient(135deg, var(--gold), var(--gold-light));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* ── Grille bento asymétrique ─────────────────────────── */
.testimonials-track {
  display: grid;
  grid-template-columns: 1.6fr 1fr;
  grid-template-rows: auto auto;
  gap: 20px;
  max-width: 960px;
  margin: 0 auto;
}

/* Card 1 : grande, colonne gauche, prend les 2 lignes */
.t-card:nth-child(1) {
  grid-row: 1 / 3;
}
/* Card 2 : petite, haut droite */
.t-card:nth-child(2) {
  grid-row: 1;
}
/* Card 3 : petite, milieu droite */
.t-card:nth-child(3) {
  grid-row: 2;
}
/* Card 4 : large, en bas — pleine largeur */
.t-card:nth-child(4) {
  grid-column: 1 / 3;
}

/* ── Card ─────────────────────────────────────────────── */
.t-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 20px;
  padding: 32px 30px 28px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  position: relative;
  overflow: hidden;
  transition: transform 0.35s ease, border-color 0.35s ease, box-shadow 0.35s ease;
}
.t-card:hover {
  transform: translateY(-4px);
  border-color: rgba(192,154,48,0.3);
  box-shadow: 0 20px 56px rgba(0,0,0,0.45), 0 0 32px rgba(192,154,48,0.08);
}

/* Subtil gradient de fond au hover */
.t-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse at 20% 0%, rgba(192,154,48,0.04) 0%, transparent 65%);
  opacity: 0;
  transition: opacity 0.4s ease;
  pointer-events: none;
}
.t-card:hover::before { opacity: 1; }

/* ── Guillemet décoratif ──────────────────────────────── */
.t-mark {
  font-family: Georgia, 'Times New Roman', serif;
  font-size: 72px;
  line-height: 0.8;
  color: var(--gold);
  opacity: 0.25;
  display: block;
  margin-bottom: -8px;
  user-select: none;
}

/* ── Étoiles ──────────────────────────────────────────── */
.t-stars {
  color: var(--gold);
  font-size: 12px;
  letter-spacing: 3px;
}

/* ── Quote ────────────────────────────────────────────── */
.t-quote {
  color: var(--gray-light);
  font-size: 14px;
  line-height: 1.8;
  font-style: italic;
  flex: 1;
}

/* ── Footer ───────────────────────────────────────────── */
.t-footer {
  display: flex;
  align-items: center;
  gap: 14px;
  padding-top: 20px;
  border-top: 1px solid var(--border);
  margin-top: auto;
}

/* Avatar circulaire — initiales ou photo */
.t-avatar {
  width: 44px; height: 44px;
  border-radius: 50%;
  background: linear-gradient(135deg, rgba(192,154,48,0.18), rgba(192,154,48,0.06));
  border: 1px solid rgba(192,154,48,0.22);
  background-size: cover;
  background-position: center top;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  font-weight: 700;
  color: var(--gold);
  letter-spacing: 0.5px;
  flex-shrink: 0;
}

.t-author {
  display: flex;
  flex-direction: column;
  gap: 3px;
}
.author-name {
  font-size: 13px;
  font-weight: 700;
  color: var(--white);
  line-height: 1.2;
}
.author-role {
  font-size: 11px;
  color: var(--gray-mid);
  letter-spacing: 0.2px;
}

/* ── Responsive ───────────────────────────────────────── */
@media (max-width: 860px) {
  .testimonials-track {
    grid-template-columns: 1fr 1fr;
    max-width: 100%;
  }
  .t-card:nth-child(1) { grid-row: auto; }
  .t-card:nth-child(4) { grid-column: auto; }
}
@media (max-width: 540px) {
  .testimonials-section { padding: 60px 0; }
  .testimonials-track { grid-template-columns: 1fr; gap: 14px; }
  .t-card:nth-child(1),
  .t-card:nth-child(4) { grid-column: auto; grid-row: auto; }
}
</style>
