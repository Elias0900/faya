<template>
  <section id="testimonials" class="testimonials-section">
    <div class="container">
      <div class="section-header reveal">
        <span class="section-tag">Témoignages</span>
        <h2 class="section-title">Ce que disent<br /><span class="gold-gradient">mes joueurs</span></h2>
      </div>

      <div class="testimonials-track">
        <article
          v-for="(t, i) in testimonials"
          :key="i"
          class="t-card reveal"
          :style="{ transitionDelay: `${i * 0.1}s` }"
        >
          <!-- Photo ou avatar -->
          <div
            class="t-thumb"
            :style="t.photo ? { backgroundImage: `url(${t.photo})` } : {}"
          >
            <span v-if="!t.photo" class="t-emoji">{{ t.avatar }}</span>
            <div class="t-thumb-fade"></div>
          </div>

          <!-- Panneau info — les éléments toujours visibles sont en haut -->
          <div class="t-infos">
            <div class="t-stars">
              <span v-for="s in 5" :key="s">★</span>
            </div>
            <div class="t-author">
              <span class="author-name">{{ t.name }}</span>
              <span class="author-role">{{ t.role }}</span>
            </div>

            <!-- Révélé au hover -->
            <div class="t-sep"></div>
            <p class="t-quote">"{{ t.text }}"</p>
            <span class="t-verified">Témoignage vérifié <span class="check-icon">✓</span></span>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const testimonials = [
  {
    text: "En 6 mois j'ai progressé plus qu'en 3 ans de club. La méthode est claire, exigeante et vraiment adaptée à mon niveau.",
    name: 'Thomas R.',
    role: 'Joueur U18 · Rennes',
    avatar: '🧑',
    photo: null,
  },
  {
    text: "Ce qui m'a surpris c'est l'approche mentale. On ne parle pas que de technique, on travaille la tête. Ça change tout.",
    name: 'Camille D.',
    role: 'Joueuse senior · Brest',
    avatar: '👩',
    photo: null,
  },
  {
    text: "J'ai intégré l'équipe première de mon club après 4 mois de coaching. Résultats concrets, coach vraiment investi.",
    name: 'Kévin M.',
    role: 'Pivot · Lorient',
    avatar: '🧔',
    photo: null,
  },
  {
    text: "La flexibilité des horaires et le suivi entre les séances via messages font vraiment la différence. Très pro.",
    name: 'Sophie L.',
    role: 'Débutante · Quimper',
    avatar: '👱‍♀️',
    photo: null,
  },
  {
    text: "Mon fils a gagné en confiance sur le terrain et en dehors. Le coach sait parler aux jeunes. Je recommande à 100%.",
    name: 'Marc B.',
    role: 'Parent · Saint-Brieuc',
    avatar: '👨',
    photo: null,
  },
  {
    text: "Programme Elite ultra-complet. Analyse vidéo, physique, nutrition — tout est inclus et vraiment suivi. Top niveau.",
    name: 'Alexis G.',
    role: 'Meneur · Vannes',
    avatar: '🧒',
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
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 16px;
}
.section-title {
  font-size: clamp(24px, 3.2vw, 40px);
  font-weight: 900;
  line-height: 1.1;
  letter-spacing: -1px;
}
.gold-gradient {
  background: linear-gradient(135deg, var(--gold), var(--gold-light));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* ── Grid ─────────────────────────────────────────────── */
.testimonials-track {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

/* ── Card ─────────────────────────────────────────────── */
.t-card {
  position: relative;
  height: 360px;
  border-radius: 16px;
  overflow: hidden;
  border: 1px solid var(--border);
  cursor: default;
  /* intègre la transition reveal + les effets hover */
  transition:
    opacity 0.6s ease,
    transform 0.6s ease,
    border-color 0.35s ease,
    box-shadow 0.35s ease;
}
.t-card:hover {
  border-color: rgba(192,154,48,0.4);
  box-shadow: 0 12px 48px rgba(0,0,0,0.5), 0 0 28px rgba(192,154,48,0.1);
}

/* ── Thumb ────────────────────────────────────────────── */
.t-thumb {
  height: 215px;
  background: linear-gradient(160deg, #1c1200 0%, #0d0d0d 45%, #1a0a00 100%) no-repeat center;
  background-size: cover;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  flex-shrink: 0;
}
/* Pour ajouter une photo : mettez t.photo = '/testimonials/thomas.jpg' */
.t-thumb-fade {
  position: absolute;
  bottom: 0; left: 0; right: 0;
  height: 56px;
  background: linear-gradient(transparent, var(--bg-card));
  pointer-events: none;
}
.t-emoji {
  font-size: 68px;
  position: relative;
  z-index: 1;
  filter: drop-shadow(0 4px 20px rgba(0,0,0,0.6));
}

/* ── Info panel ───────────────────────────────────────── */
.t-infos {
  background: var(--bg-card);
  padding: 20px 24px 24px;
  display: flex;
  flex-direction: column;
  /* pas de justify-content flex-end — le contenu visible est en haut */
  transform: translateY(0);
  transition: transform 0.45s 0.05s cubic-bezier(.17,.67,.5,1.03);
}
.t-card:hover .t-infos {
  transform: translateY(-215px);
}

/* Toujours visibles (en haut du panneau) */
.t-stars {
  color: var(--gold);
  font-size: 14px;
  letter-spacing: 3px;
  margin-bottom: 10px;
  flex-shrink: 0;
}
.t-author {
  display: flex;
  flex-direction: column;
  gap: 4px;
  flex-shrink: 0;
}
.author-name {
  font-weight: 700;
  font-size: 15px;
  color: var(--white);
}
.author-role {
  font-size: 12px;
  color: var(--gray-mid);
  letter-spacing: 0.3px;
}

/* Révélés au hover (en dessous) */
.t-sep {
  height: 1px;
  background: linear-gradient(to right, rgba(192,154,48,0.5), transparent);
  margin: 18px 0 16px;
  flex-shrink: 0;
  opacity: 0;
  transition: opacity 0.3s 0.15s ease;
}
.t-quote {
  color: var(--gray-light);
  font-size: 14px;
  line-height: 1.75;
  font-style: italic;
  margin: 0 0 12px;
  flex-shrink: 0;
  opacity: 0;
  transform: translateY(8px);
  transition: opacity 0.3s 0.2s ease, transform 0.3s 0.2s ease;
}
.t-verified {
  font-size: 12px;
  color: var(--gray-mid);
  letter-spacing: 0.3px;
  flex-shrink: 0;
  opacity: 0;
  transition: opacity 0.3s 0.28s ease;
}
.check-icon { color: var(--gold); font-weight: 700; }

.t-card:hover .t-sep     { opacity: 1; }
.t-card:hover .t-quote   { opacity: 1; transform: translateY(0); }
.t-card:hover .t-verified { opacity: 1; }

/* ── Responsive ───────────────────────────────────────── */
@media (max-width: 960px) {
  .testimonials-section { padding: 72px 0; }
  .testimonials-track { grid-template-columns: repeat(2, 1fr); gap: 20px; }
  .section-header { margin-bottom: 40px; }
}
@media (max-width: 600px) {
  .testimonials-section { padding: 56px 0; }
  .testimonials-track { grid-template-columns: 1fr; gap: 16px; }

  /* Mobile : affichage statique complet, pas d'animation hover */
  .t-card { height: auto; }
  .t-thumb { height: 160px; }
  .t-infos { transform: none !important; transition: none; }
  .t-sep, .t-quote, .t-verified { opacity: 1 !important; transform: none !important; }
}
</style>
