<template>
  <section id="hero" class="hero">
    <div class="hero-bg">
      <div class="orb orb-1"></div>
      <div class="orb orb-2"></div>
      <div class="orb orb-3"></div>
      <div class="orb orb-4"></div>
      <div class="bokeh-field">
        <span class="dot dot-1"></span>
        <span class="dot dot-2"></span>
        <span class="dot dot-3"></span>
        <span class="dot dot-4"></span>
        <span class="dot dot-5"></span>
        <span class="dot dot-6"></span>
        <span class="dot dot-7"></span>
      </div>
      <div class="vignette"></div>
    </div>

    <div class="container hero-inner">
      <div class="hero-content">
        <div class="hero-badge reveal">
          <span class="badge-dot"></span>
          Coach Certifié · Bretagne
        </div>
        <h1 class="hero-title reveal">
          Élève ton jeu.<br />
          <span class="gold-gradient">Dépasse tes limites.</span>
        </h1>
        <p class="hero-sub reveal">
          Coaching basketball personnalisé — technique, mental et physique.<br />
          De débutant à compétiteur, je t'accompagne à chaque étape.
        </p>
        <div class="hero-actions reveal">
          <a href="#contact" class="btn-primary">
            Réserver une séance
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </a>
          <a href="#services" class="btn-ghost">Voir les programmes</a>
        </div>
      </div>

      <!-- Photo section -->
      <div class="hero-visual">
        <div class="photo-frame">
          <!-- Glow derrière la photo -->
          <div class="photo-glow"></div>

          <!-- Cadre photo -->
          <div class="photo-container">
            <img
              :src="photoSrc"
              alt="Coach Basketball"
              class="coach-photo"
              @error="onImgError"
            />
            <div class="photo-placeholder"></div>
            <div class="photo-gradient-overlay"></div>
          </div>

          <!-- Badge flottant haut-droite -->
          <div class="float-badge float-badge-top">
            <span class="fbadge-icon">🏆</span>
            <div class="fbadge-text">
              <span class="fbadge-val">8+</span>
              <span class="fbadge-label">ans coaching</span>
            </div>
          </div>

          <!-- Badge flottant bas-gauche -->
          <div class="float-badge float-badge-bottom">
            <span class="fbadge-icon">🎯</span>
            <div class="fbadge-text">
              <span class="fbadge-val">120+</span>
              <span class="fbadge-label">joueurs coachés</span>
            </div>
          </div>

          <!-- Anneau décoratif -->
          <div class="deco-ring"></div>
        </div>
      </div>
    </div>

    <div class="scroll-hint">
      <div class="scroll-line"></div>
      <span>Scroll</span>
    </div>
  </section>
</template>

<script setup lang="ts">
// Remplace /coach.jpg par le chemin de ta photo dans le dossier public/
const photoSrc = '/coach.jpg'

function onImgError(e: Event) {
  const img = e.target as HTMLImageElement
  img.style.display = 'none'
}
</script>

<style scoped>
/* ── Layout ───────────────────────────────────────────── */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
}
.hero-bg {
  position: absolute;
  inset: 0;
  pointer-events: none;
}
/* ── Aurora orbs ──────────────────────────────────────── */
.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  will-change: transform, opacity;
}
.orb-1 {
  width: 700px; height: 700px;
  background: radial-gradient(circle, rgb(15 69 65 / 0.51) 0%, transparent 85%);
  top: -260px; right: -180px;
  animation: orb-drift-1 12s ease-in-out infinite alternate;
}
.orb-2 {
  width: 500px; height: 500px;
  background: radial-gradient(circle, rgb(92 55 3 / 0.51) 0%, transparent 85%);
  bottom: -160px; left: -140px;
  animation: orb-drift-2 15s ease-in-out infinite alternate;
}
.orb-3 {
  width: 380px; height: 380px;
  background: radial-gradient(circle, rgb(211 134 14 / 0.44) 0%, transparent 85%);
  top: 30%; left: 20%;
  animation: orb-drift-3 18s ease-in-out infinite alternate;
}
.orb-4 {
  width: 280px; height: 280px;
  background: radial-gradient(circle, rgb(106 108 166 / 0.47) 0%, transparent 85%);
  bottom: 10%; right: 15%;
  animation: orb-drift-4 11s ease-in-out infinite alternate;
}
@keyframes orb-drift-1 {
  from { transform: translate(0,0) scale(1); opacity: 0.8; }
  to   { transform: translate(40px, 30px) scale(1.12); opacity: 1; }
}
@keyframes orb-drift-2 {
  from { transform: translate(0,0) scale(1); opacity: 0.7; }
  to   { transform: translate(-30px, -20px) scale(1.08); opacity: 1; }
}
@keyframes orb-drift-3 {
  from { transform: translate(0,0) scale(0.95); opacity: 0.5; }
  to   { transform: translate(20px, -30px) scale(1.1); opacity: 0.8; }
}
@keyframes orb-drift-4 {
  from { transform: translate(0,0) scale(1); opacity: 0.6; }
  to   { transform: translate(-15px, 20px) scale(1.15); opacity: 0.9; }
}

/* ── Bokeh light dots ─────────────────────────────────── */
.bokeh-field {
  position: absolute;
  inset: 0;
  pointer-events: none;
}
.dot {
  position: absolute;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(201,162,39,0.55) 0%, transparent 70%);
  filter: blur(2px);
  will-change: opacity, transform;
}
.dot-1 { width: 6px;  height: 6px;  top: 18%;  left: 8%;   animation: twinkle 4s 0.0s ease-in-out infinite; }
.dot-2 { width: 4px;  height: 4px;  top: 35%;  left: 55%;  animation: twinkle 5s 0.7s ease-in-out infinite; }
.dot-3 { width: 8px;  height: 8px;  top: 62%;  left: 22%;  animation: twinkle 6s 1.4s ease-in-out infinite; background: radial-gradient(circle, rgba(255,140,0,0.5) 0%, transparent 70%); }
.dot-4 { width: 5px;  height: 5px;  top: 10%;  left: 72%;  animation: twinkle 4.5s 2.1s ease-in-out infinite; }
.dot-5 { width: 7px;  height: 7px;  top: 78%;  left: 80%;  animation: twinkle 7s 0.3s ease-in-out infinite; background: radial-gradient(circle, rgba(255,180,0,0.45) 0%, transparent 70%); }
.dot-6 { width: 4px;  height: 4px;  top: 50%;  left: 92%;  animation: twinkle 5.5s 1.8s ease-in-out infinite; }
.dot-7 { width: 6px;  height: 6px;  top: 88%;  left: 42%;  animation: twinkle 4.2s 0.9s ease-in-out infinite; }
@keyframes twinkle {
  0%,100% { opacity: 0.15; transform: scale(0.8); }
  50%      { opacity: 0.9;  transform: scale(1.3); }
}

/* ── Vignette ─────────────────────────────────────────── */
.vignette {
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse at 50% 50%, transparent 40%, rgba(8,8,8,0.65) 100%);
  pointer-events: none;
}

.hero-inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  padding-top: 100px;
  padding-bottom: 60px;
}

/* ── Texte gauche ─────────────────────────────────────── */
.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--gold-dim);
  border: 1px solid rgba(201,162,39,0.3);
  color: var(--gold-light);
  font-size: 13px; font-weight: 600;
  letter-spacing: 1px; text-transform: uppercase;
  padding: 8px 16px; border-radius: 100px;
  margin-bottom: 24px;
}
.badge-dot {
  width: 7px; height: 7px;
  background: var(--gold); border-radius: 50%;
  animation: pulse-dot 2s ease-in-out infinite;
}
@keyframes pulse-dot {
  0%,100% { opacity:1; transform:scale(1); }
  50%      { opacity:0.5; transform:scale(0.8); }
}
.hero-title {
  font-size: clamp(42px,6vw,72px);
  font-weight: 900; line-height: 1.05;
  letter-spacing: -2px; margin-bottom: 24px;
  color: var(--white);
}
.gold-gradient {
  background: linear-gradient(135deg, var(--gold) 0%, var(--gold-light) 50%, #ff9500 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.hero-sub {
  font-size: 17px; color: var(--gray-light);
  line-height: 1.7; margin-bottom: 40px; max-width: 480px;
}
.hero-actions {
  display: flex; gap: 16px;
  align-items: center; flex-wrap: wrap;
}
.btn-primary {
  display: inline-flex; align-items: center; gap: 8px;
  background: var(--gold); color: #000;
  text-decoration: none; font-weight: 700; font-size: 15px;
  padding: 14px 28px; border-radius: 10px;
  transition: all 0.3s ease;
  box-shadow: 0 4px 24px rgba(201,162,39,0.35);
}
.btn-primary:hover {
  background: var(--gold-light);
  transform: translateY(-2px);
  box-shadow: 0 8px 32px rgba(201,162,39,0.5);
}
.btn-ghost {
  display: inline-flex; align-items: center;
  color: var(--gray-light); text-decoration: none;
  font-weight: 500; font-size: 15px;
  padding: 14px 20px; border-radius: 10px;
  border: 1px solid var(--border); transition: all 0.3s;
}
.btn-ghost:hover { color: var(--white); border-color: rgba(255,255,255,0.2); }

/* ── Photo droite ─────────────────────────────────────── */
.hero-visual {
  display: flex;
  justify-content: center;
  align-items: center;
  animation: photo-entry 1s cubic-bezier(0.16,1,0.3,1) both;
  animation-delay: 0.3s;
}
@keyframes photo-entry {
  from { opacity: 0; transform: translateY(40px) scale(0.96); }
  to   { opacity: 1; transform: translateY(0) scale(1); }
}

.photo-frame {
  position: relative;
  width: 340px;
  animation: photo-float 6s ease-in-out infinite;
}
@keyframes photo-float {
  0%,100% { transform: translateY(0px); }
  50%      { transform: translateY(-14px); }
}

/* Glow derrière */
.photo-glow {
  position: absolute;
  inset: -30px;
  background: radial-gradient(ellipse at 60% 40%, rgba(201,162,39,0.28), transparent 65%);
  filter: blur(30px);
  border-radius: 50%;
  animation: glow-breathe 4s ease-in-out infinite;
  z-index: 0;
}
@keyframes glow-breathe {
  0%,100% { opacity: 0.7; transform: scale(1); }
  50%      { opacity: 1;   transform: scale(1.08); }
}

/* Cadre photo */
.photo-container {
  position: relative;
  z-index: 1;
  border-radius: 24px;
  overflow: hidden;
  aspect-ratio: 3/4;
  border: 1px solid rgba(201,162,39,0.35);
  box-shadow:
    0 0 0 1px rgba(201,162,39,0.1),
    0 40px 80px rgba(0,0,0,0.6),
    inset 0 1px 0 rgba(255,255,255,0.05);
  animation: border-glow 4s ease-in-out infinite;
}
@keyframes border-glow {
  0%,100% { box-shadow: 0 0 0 1px rgba(201,162,39,0.1), 0 40px 80px rgba(0,0,0,0.6), 0 0 40px rgba(201,162,39,0.1); }
  50%      { box-shadow: 0 0 0 1px rgba(201,162,39,0.25), 0 40px 80px rgba(0,0,0,0.6), 0 0 60px rgba(201,162,39,0.2); }
}

.coach-photo {
  width: 100%; height: 100%;
  object-fit: cover;
  object-position: center top;
  display: block;
  transition: transform 0.6s ease, filter 0.4s ease;
  filter: brightness(0.92) contrast(1.05);
}
.photo-container:hover .coach-photo {
  transform: scale(1.04);
  filter: brightness(1) contrast(1.05);
}

/* Placeholder si pas d'image */
.photo-placeholder {
  position: absolute;
  inset: 0;
  background: linear-gradient(160deg, #1a1400 0%, #0d0d0d 40%, #1a0a00 100%);
  z-index: -1;
}

/* Dégradé en bas de la photo */
.photo-gradient-overlay {
  position: absolute;
  bottom: 0; left: 0; right: 0;
  height: 45%;
  background: linear-gradient(transparent, rgba(8,8,8,0.75));
  pointer-events: none;
}

/* Badges flottants */
.float-badge {
  position: absolute;
  display: flex;
  align-items: center;
  gap: 10px;
  background: rgba(10,10,10,0.85);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(201,162,39,0.25);
  border-radius: 14px;
  padding: 10px 16px;
  z-index: 3;
  box-shadow: 0 8px 32px rgba(0,0,0,0.4);
  white-space: nowrap;
  cursor: default;
  transition:
    border-color 0.35s ease,
    box-shadow 0.35s ease,
    background 0.35s ease,
    transform 0.4s cubic-bezier(0.34,1.56,0.64,1);
}
.float-badge:hover {
  border-color: rgba(201,162,39,0.6);
  background: rgba(18,14,0,0.92);
  box-shadow:
    0 12px 40px rgba(0,0,0,0.55),
    0 0 24px rgba(201,162,39,0.2),
    inset 0 1px 0 rgba(201,162,39,0.15);
  transform: translateY(-5px) scale(1.05);
  animation-play-state: paused;
}
.float-badge:hover .fbadge-icon {
  transform: scale(1.2) rotate(-5deg);
  display: inline-block;
}
.fbadge-icon {
  transition: transform 0.35s cubic-bezier(0.34,1.56,0.64,1);
}
.float-badge-top {
  top: 28px; right: -28px;
  animation: badge-float-top 5s ease-in-out infinite;
  animation-delay: 0.8s;
}
.float-badge-bottom {
  bottom: 52px; left: -28px;
  animation: badge-float-bottom 5s ease-in-out infinite;
  animation-delay: 1.6s;
}
@keyframes badge-float-top {
  0%,100% { transform: translate(0,0); }
  50%      { transform: translate(4px,-8px); }
}
@keyframes badge-float-bottom {
  0%,100% { transform: translate(0,0); }
  50%      { transform: translate(-4px,6px); }
}
.fbadge-icon { font-size: 20px; }
.fbadge-text { display: flex; flex-direction: column; line-height: 1.2; }
.fbadge-val {
  font-size: 16px; font-weight: 800;
  background: linear-gradient(135deg, var(--gold), var(--gold-light));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.fbadge-label { font-size: 11px; color: var(--gray-light); letter-spacing: 0.3px; }

/* Anneau décoratif */
.deco-ring {
  position: absolute;
  inset: -16px;
  border-radius: 28px;
  border: 1px dashed rgba(201,162,39,0.15);
  z-index: 0;
  animation: ring-rotate 20s linear infinite;
}
@keyframes ring-rotate {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}

/* ── Scroll hint ──────────────────────────────────────── */
.scroll-hint {
  position: absolute;
  bottom: 32px; left: 50%;
  transform: translateX(-50%);
  display: flex; flex-direction: column;
  align-items: center; gap: 8px;
  color: var(--gray-mid); font-size: 11px;
  letter-spacing: 2px; text-transform: uppercase;
}
.scroll-line {
  width: 1px; height: 40px;
  background: linear-gradient(to bottom, var(--gold), transparent);
  animation: scroll-line 2s ease-in-out infinite;
}
@keyframes scroll-line {
  0%,100% { opacity:1; transform:scaleY(1); }
  50%      { opacity:0.4; transform:scaleY(0.6); }
}

/* ── Responsive ───────────────────────────────────────── */
@media (max-width: 960px) {
  .hero-inner { gap: 32px; }
  .photo-frame { width: 260px; }
  .float-badge-top  { right: -16px; }
  .float-badge-bottom { left: -16px; }
  .hero-actions { flex-direction: column; align-items: flex-start; }
  .btn-primary, .btn-ghost { width: 100%; justify-content: center; }
}
@media (max-width: 680px) {
  .hero-inner {
    grid-template-columns: 1fr;
    text-align: center;
    padding-top: 110px; padding-bottom: 80px;
  }
  .hero-title { letter-spacing: -1px; }
  .hero-sub { margin: 0 auto 36px; max-width: 100%; }
  .hero-actions { justify-content: center; flex-direction: column; align-items: stretch; }
  .btn-primary, .btn-ghost { justify-content: center; }
  .hero-visual { display: none; }
  .hero-badge { margin: 0 auto 20px; }
}
</style>
