<template>
  <section id="stats" class="stats-section">
    <div class="container">
      <div class="stats-grid">
        <div
          v-for="(stat, i) in stats"
          :key="i"
          class="stat-card reveal"
          :style="{ transitionDelay: `${i * 0.12}s` }"
        >
          <div class="stat-icon">{{ stat.icon }}</div>
          <div class="stat-number">
            <span class="count" :data-target="stat.value">{{ animatedValues[i] }}</span>
            <span class="stat-suffix">{{ stat.suffix }}</span>
          </div>
          <div class="stat-label">{{ stat.label }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const stats = [
  { icon: '🏆', value: 8,   suffix: '+', label: "Années d'expérience" },
  { icon: '🎯', value: 120, suffix: '+', label: 'Joueurs coachés' },
  { icon: '📈', value: 94,  suffix: '%', label: 'Taux de progression' },
  { icon: '🥇', value: 15,  suffix: '',  label: 'Titres régionaux' },
]

const animatedValues = ref(stats.map(() => 0))

function animateCount(index: number, target: number, duration = 1800) {
  const start = performance.now()
  const step = (now: number) => {
    const progress = Math.min((now - start) / duration, 1)
    const ease = 1 - Math.pow(1 - progress, 3)
    animatedValues.value[index] = Math.round(ease * target)
    if (progress < 1) requestAnimationFrame(step)
  }
  requestAnimationFrame(step)
}

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          stats.forEach((s, i) => animateCount(i, s.value))
          observer.disconnect()
        }
      })
    },
    { threshold: 0.3 }
  )
  const section = document.querySelector('#stats')
  if (section) observer.observe(section)
})
</script>

<style scoped>
.stats-section {
  padding: 80px 0;
  position: relative;
}
.stats-section::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, transparent 0%, rgba(192,154,48,0.04) 50%, transparent 100%);
  pointer-events: none;
}
.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1px;
  background: var(--border);
  border-radius: var(--radius-lg);
  overflow: hidden;
}
.stat-card {
  background: var(--bg-card);
  padding: 48px 32px;
  text-align: center;
  transition: background 0.3s;
  position: relative;
}
.stat-card::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 2px;
  background: var(--gold);
  transition: width 0.4s ease;
}
.stat-card:hover {
  background: #1a1a1a;
}
.stat-card:hover::after {
  width: 60%;
}
.stat-icon {
  font-size: 32px;
  margin-bottom: 16px;
}
.stat-number {
  display: flex;
  align-items: baseline;
  justify-content: center;
  gap: 2px;
  margin-bottom: 8px;
}
.count {
  font-size: 40px;
  font-weight: 900;
  background: linear-gradient(135deg, var(--gold), var(--gold-light));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  line-height: 1;
}
.stat-suffix {
  font-size: 22px;
  font-weight: 700;
  color: var(--gold);
}
.stat-label {
  font-size: 13px;
  color: var(--gray-light);
  font-weight: 500;
  letter-spacing: 0.5px;
}

@media (max-width: 900px) {
  .stats-section { padding: 60px 0; }
}
@media (max-width: 768px) {
  .stats-grid { grid-template-columns: repeat(2, 1fr); }
  .stat-card { padding: 32px 16px; }
  .count { font-size: 40px; }
  .stat-suffix { font-size: 22px; }
}
@media (max-width: 420px) {
  .stat-card { padding: 24px 12px; }
  .count { font-size: 34px; }
  .stat-icon { font-size: 24px; }
}
</style>
