<template>
  <section id="services" class="services-section">
    <div class="container">
      <div class="section-header reveal">
        <span class="section-tag">Programmes</span>
        <h2 class="section-title">Un coaching taillé<br /><span class="gold-gradient">pour ton niveau</span></h2>
        <p class="section-sub">Chaque programme est construit autour de tes objectifs, ton rythme et ta progression.</p>
      </div>

      <div class="services-grid">
        <div
          v-for="(service, i) in services"
          :key="i"
          class="service-card reveal"
          :class="{ featured: service.featured }"
          :style="{ transitionDelay: `${i * 0.15}s` }"
        >
          <div v-if="service.featured" class="featured-badge">Le plus populaire</div>
          <div class="service-icon">{{ service.icon }}</div>
          <h3 class="service-name">{{ service.name }}</h3>
          <p class="service-desc">{{ service.desc }}</p>
          <ul class="service-features">
            <li v-for="f in service.features" :key="f">
              <span class="check">✓</span>{{ f }}
            </li>
          </ul>
          <div class="service-price">
            <span class="price-amount">{{ service.price }}</span>
            <span class="price-period">{{ service.period }}</span>
          </div>
          <a href="#contact" class="service-btn" :class="{ 'btn-gold': service.featured }">
            {{ service.featured ? 'Commencer maintenant' : 'En savoir plus' }}
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const services = [
  {
    icon: '🌱',
    name: 'Débutant',
    desc: 'Pose les bases solides du basketball et progresse à ton rythme.',
    features: ['Fondamentaux techniques', '2 séances / semaine', 'Suivi personnalisé', 'Bilan mensuel'],
    price: '80€',
    period: '/ séance',
    featured: false,
  },
  {
    icon: '🔥',
    name: 'Compétiteur',
    desc: 'Un programme intensif pour viser la performance et dominer sur le terrain.',
    features: ['Technique avancée', '4 séances / semaine', 'Préparation physique', 'Analyse vidéo', 'Nutrition sportive', 'Accès illimité coach'],
    price: '299€',
    period: '/ mois',
    featured: true,
  },
  {
    icon: '⚡',
    name: 'Elite',
    desc: 'Pour les joueurs en club visant le niveau régional et national.',
    features: ['Programme sur-mesure', 'Séances illimitées', 'Prépa mentale', 'Recrutement club'],
    price: '450€',
    period: '/ mois',
    featured: false,
  },
]
</script>

<style scoped>
.services-section {
  padding: 100px 0;
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
  font-size: clamp(32px, 4vw, 52px);
  font-weight: 900;
  line-height: 1.1;
  letter-spacing: -1px;
  margin-bottom: 16px;
}
.gold-gradient {
  background: linear-gradient(135deg, var(--gold), var(--gold-light));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.section-sub {
  color: var(--gray-light);
  font-size: 16px;
  max-width: 500px;
  margin: 0 auto;
  line-height: 1.7;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  align-items: start;
}
.service-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 40px 32px;
  position: relative;
  transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
}
.service-card:hover {
  transform: translateY(-6px);
  border-color: rgba(201,162,39,0.3);
  box-shadow: var(--shadow-gold);
}
.service-card.featured {
  background: linear-gradient(145deg, #1a1600, #0f0f0f);
  border-color: var(--gold);
  box-shadow: 0 0 50px rgba(201,162,39,0.18);
}
.featured-badge {
  position: absolute;
  top: -14px;
  left: 50%;
  transform: translateX(-50%);
  background: var(--gold);
  color: #000;
  font-size: 11px;
  font-weight: 800;
  letter-spacing: 1px;
  text-transform: uppercase;
  padding: 6px 18px;
  border-radius: 100px;
  white-space: nowrap;
}
.service-icon {
  font-size: 36px;
  margin-bottom: 20px;
}
.service-name {
  font-size: 22px;
  font-weight: 800;
  margin-bottom: 12px;
  color: var(--white);
}
.service-desc {
  color: var(--gray-light);
  font-size: 14px;
  line-height: 1.6;
  margin-bottom: 28px;
}
.service-features {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 32px;
}
.service-features li {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 14px;
  color: var(--gray-light);
}
.check {
  color: var(--gold);
  font-weight: 700;
  flex-shrink: 0;
}
.service-price {
  margin-bottom: 24px;
  display: flex;
  align-items: baseline;
  gap: 6px;
}
.price-amount {
  font-size: 40px;
  font-weight: 900;
  color: var(--white);
}
.price-period {
  font-size: 14px;
  color: var(--gray-light);
}
.service-btn {
  display: block;
  text-align: center;
  padding: 14px;
  border-radius: 10px;
  border: 1px solid var(--border);
  color: var(--gray-light);
  text-decoration: none;
  font-weight: 600;
  font-size: 14px;
  transition: all 0.3s;
}
.service-btn:hover {
  border-color: rgba(255,255,255,0.2);
  color: var(--white);
}
.service-btn.btn-gold {
  background: var(--gold);
  color: #000;
  border-color: var(--gold);
}
.service-btn.btn-gold:hover {
  background: var(--gold-light);
}

@media (max-width: 960px) {
  .services-section { padding: 72px 0; }
  .services-grid {
    grid-template-columns: 1fr;
    max-width: 520px;
    margin: 0 auto;
  }
  .section-header { margin-bottom: 48px; }
}
@media (max-width: 640px) {
  .services-section { padding: 56px 0; }
  .services-grid { max-width: 100%; }
  .service-card { padding: 32px 24px; }
  .section-header { margin-bottom: 36px; }
}
</style>
