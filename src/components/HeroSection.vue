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

      <div class="hero-visual">
        <div class="photo-frame">
          <div class="photo-glow"></div>
          <div class="photo-container">
            <img :src="photoSrc" alt="Coach Basketball" class="coach-photo" @error="onImgError" />
            <div class="photo-placeholder"></div>
            <div class="photo-gradient-overlay"></div>
          </div>
          <div class="float-badge float-badge-top">
            <span class="fbadge-icon">🏆</span>
            <div class="fbadge-text">
              <span class="fbadge-val">8+</span>
              <span class="fbadge-label">ans coaching</span>
            </div>
          </div>
          <div class="float-badge float-badge-bottom">
            <span class="fbadge-icon">🎯</span>
            <div class="fbadge-text">
              <span class="fbadge-val">120+</span>
              <span class="fbadge-label">joueurs coachés</span>
            </div>
          </div>
          <div class="deco-ring"></div>
        </div>

        <div class="cert-badge reveal">
          <span class="cert-dot"></span>
          <span class="cert-text">Coach Certifié · Bretagne</span>
        </div>
      </div>
    </div>

    <div class="scroll-hint">
      <div class="scroll-line"></div>
      <span>MAKE IT HAPPEN</span>
    </div>
  </section>
</template>

<script setup lang="ts">
const photoSrc = '/coach.jpg'
function onImgError(e: Event) {
  const img = e.target as HTMLImageElement
  img.style.display = 'none'
}
</script>

<style scoped>
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

/* ── Aurora — très sombres, juste un souffle d'or ─────── */
.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(110px);
  will-change: transform, opacity;
}
.orb-1 {
  width: 700px; height: 700px;
  background: radial-gradient(circle, rgba(95,60,4,0.32) 0%, transparent 80%);
  top: -260px; right: -180px;
  animation: orb-drift-1 12s ease-in-out infinite alternate;
}
.orb-2 {
  width: 500px; height: 500px;
  background: radial-gradient(circle, rgba(65,42,3,0.26) 0%, transparent 80%);
  bottom: -160px; left: -140px;
  animation: orb-drift-2 15s ease-in-out infinite alternate;
}
.orb-3 {
  width: 380px; height: 380px;
  background: radial-gradient(circle, rgba(140,88,6,0.22) 0%, transparent 80%);
  top: 30%; left: 20%;
  animation: orb-drift-3 18s ease-in-out infinite alternate;
}
.orb-4 {
  width: 280px; height: 280px;
  background: radial-gradient(circle, rgba(48,32,8,0.18) 0%, transparent 80%);
  bottom: 10%; right: 15%;
  animation: orb-drift-4 11s ease-in-out infinite alternate;
}
@keyframes orb-drift-1 {
  from { transform: translate(0,0) scale(1);    opacity: 0.8; }
  to   { transform: translate(40px,30px) scale(1.12); opacity: 1; }
}
@keyframes orb-drift-2 {
  from { transform: translate(0,0) scale(1);    opacity: 0.7; }
  to   { transform: translate(-30px,-20px) scale(1.08); opacity: 1; }
}
@keyframes orb-drift-3 {
  from { transform: translate(0,0) scale(0.95); opacity: 0.5; }
  to   { transform: translate(20px,-30px) scale(1.1); opacity: 0.8; }
}
@keyframes orb-drift-4 {
  from { transform: translate(0,0) scale(1);    opacity: 0.6; }
  to   { transform: translate(-15px,20px) scale(1.15); opacity: 0.9; }
}

/* ── Bokeh dots ───────────────────────────────────────── */
.bokeh-field { position: absolute; inset: 0; pointer-events: none; }
.dot {
  position: absolute;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(192,154,48,0.5) 0%, transparent 70%);
  filter: blur(2px);
  will-change: opacity, transform;
}
.dot-1 { width: 6px; height: 6px; top: 18%; left: 8%;  animation: twinkle 4s 0.0s ease-in-out infinite; }
.dot-2 { width: 4px; height: 4px; top: 35%; left: 55%; animation: twinkle 5s 0.7s ease-in-out infinite; }
.dot-3 { width: 8px; height: 8px; top: 62%; left: 22%; animation: twinkle 6s 1.4s ease-in-out infinite; background: radial-gradient(circle, rgba(212,174,80,0.45) 0%, transparent 70%); }
.dot-4 { width: 5px; height: 5px; top: 10%; left: 72%; animation: twinkle 4.5s 2.1s ease-in-out infinite; }
.dot-5 { width: 7px; height: 7px; top: 78%; left: 80%; animation: twinkle 7s 0.3s ease-in-out infinite; background: radial-gradient(circle, rgba(192,154,48,0.4) 0%, transparent 70%); }
.dot-6 { width: 4px; height: 4px; top: 50%; left: 92%; animation: twinkle 5.5s 1.8s ease-in-out infinite; }
.dot-7 { width: 6px; height: 6px; top: 88%; left: 42%; animation: twinkle 4.2s 0.9s ease-in-out infinite; }
@keyframes twinkle {
  0%,100% { opacity: 0.15; transform: scale(0.8); }
  50%      { opacity: 0.9;  transform: scale(1.3); }
}

/* ── Vignette ─────────────────────────────────────────── */
.vignette {
  position: absolute; inset: 0;
  background: radial-gradient(ellipse at 50% 50%, transparent 40%, rgba(5,4,3,0.7) 100%);
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

/* ── Badge coach certifié ─────────────────────────────── */
@property --badge-angle {
  syntax: '<angle>';
  initial-value: 0deg;
  inherits: false;
}

.cert-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-size: 13px; font-weight: 600;
  letter-spacing: 1px; text-transform: uppercase;
  padding: 9px 18px; border-radius: 7px;
  position: relative;
  border: 1px solid transparent;
  background:
    linear-gradient(#0a0806, #0a0806) padding-box,
    conic-gradient(
      from var(--badge-angle),
      transparent              82%,
      rgba(192,154,48,0.5)     90%,
      rgba(255,240,160,0.95)   93%,
      rgba(192,154,48,0.5)     96%,
      transparent              100%
    ) border-box;
  animation: badge-border-rotate 2.8s linear infinite;
}
@keyframes badge-border-rotate { to { --badge-angle: 360deg; } }

.cert-dot, .cert-text { position: relative; z-index: 1; }
.cert-dot {
  width: 7px; height: 7px;
  background: var(--gold); border-radius: 50%;
  flex-shrink: 0;
  animation: pulse-dot 2s ease-in-out infinite;
}
.cert-text {
  background: linear-gradient(
    to right,
    var(--gold) 0%, var(--gold) 30%,
    rgba(255,248,200,0.95) 50%,
    var(--gold) 70%, var(--gold) 100%
  );
  background-size: 250% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: cert-shine 5s linear infinite;
}
@keyframes cert-shine {
  from { background-position: 200% center; }
  to   { background-position: -50% center; }
}
@keyframes pulse-dot {
  0%,100% { opacity:1; transform:scale(1); }
  50%      { opacity:0.4; transform:scale(0.75); }
}

/* ── Contenu hero ─────────────────────────────────────── */
.hero-title {
  font-size: clamp(42px,6vw,72px);
  font-weight: 900; line-height: 1.05;
  letter-spacing: -2px; margin-bottom: 24px;
  color: var(--white);
}
.gold-gradient {
  background: linear-gradient(135deg, var(--gold) 0%, var(--gold-light) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.hero-sub {
  font-size: 17px; color: var(--gray-light);
  line-height: 1.7; margin-bottom: 40px; max-width: 480px;
}
.hero-actions { display: flex; gap: 16px; align-items: center; flex-wrap: wrap; }

.btn-primary {
  display: inline-flex; align-items: center; gap: 8px;
  background: var(--gold); color: #080706;
  text-decoration: none; font-weight: 700; font-size: 15px;
  padding: 14px 28px; border-radius: 10px;
  transition: all 0.3s ease;
  box-shadow: 0 4px 24px rgba(192,154,48,0.35);
}
.btn-primary:hover {
  background: var(--gold-light);
  transform: translateY(-2px);
  box-shadow: 0 8px 32px rgba(192,154,48,0.5);
}
.btn-ghost {
  display: inline-flex; align-items: center;
  color: var(--gray-light); text-decoration: none;
  font-weight: 500; font-size: 15px;
  padding: 14px 20px; border-radius: 10px;
  border: 1px solid var(--border); transition: all 0.3s;
}
.btn-ghost:hover { color: var(--white); border-color: rgba(255,255,255,0.2); }

/* ── Photo ────────────────────────────────────────────── */
.hero-visual {
  display: flex; flex-direction: column;
  align-items: center; gap: 28px;
  animation: photo-entry 1s cubic-bezier(0.16,1,0.3,1) both;
  animation-delay: 0.3s;
}
@keyframes photo-entry {
  from { opacity: 0; transform: translateY(40px) scale(0.96); }
  to   { opacity: 1; transform: translateY(0) scale(1); }
}
.photo-frame {
  position: relative; width: 340px;
  animation: photo-float 6s ease-in-out infinite;
}
@keyframes photo-float {
  0%,100% { transform: translateY(0px); }
  50%      { transform: translateY(-14px); }
}
.photo-glow {
  position: absolute; inset: -30px;
  background: radial-gradient(ellipse at 60% 40%, rgba(192,154,48,0.25), transparent 65%);
  filter: blur(30px); border-radius: 50%;
  animation: glow-breathe 4s ease-in-out infinite; z-index: 0;
}
@keyframes glow-breathe {
  0%,100% { opacity: 0.7; transform: scale(1); }
  50%      { opacity: 1;   transform: scale(1.08); }
}
.photo-container {
  position: relative; z-index: 1;
  border-radius: 24px; overflow: hidden; aspect-ratio: 3/4;
  border: 1px solid rgba(192,154,48,0.3);
  box-shadow:
    0 0 0 1px rgba(192,154,48,0.08),
    0 40px 80px rgba(0,0,0,0.7),
    inset 0 1px 0 rgba(255,255,255,0.04);
  animation: border-glow 4s ease-in-out infinite;
}
@keyframes border-glow {
  0%,100% { box-shadow: 0 0 0 1px rgba(192,154,48,0.08), 0 40px 80px rgba(0,0,0,0.7), 0 0 40px rgba(192,154,48,0.08); }
  50%      { box-shadow: 0 0 0 1px rgba(192,154,48,0.2),  0 40px 80px rgba(0,0,0,0.7), 0 0 60px rgba(192,154,48,0.16); }
}
.coach-photo {
  width: 100%; height: 100%;
  object-fit: cover; object-position: center top; display: block;
  transition: transform 0.6s ease, filter 0.4s ease;
  filter: brightness(0.92) contrast(1.05);
}
.photo-container:hover .coach-photo {
  transform: scale(1.04); filter: brightness(1) contrast(1.05);
}
.photo-placeholder {
  position: absolute; inset: 0;
  background: linear-gradient(160deg, #150f02 0%, #0a0806 40%, #120a01 100%);
  z-index: -1;
}
.photo-gradient-overlay {
  position: absolute; bottom: 0; left: 0; right: 0; height: 45%;
  background: linear-gradient(transparent, rgba(5,4,3,0.8));
  pointer-events: none;
}

/* ── Float badges ─────────────────────────────────────── */
.float-badge {
  position: absolute;
  display: flex; align-items: center; gap: 10px;
  background: rgba(8,7,5,0.88);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(192,154,48,0.22);
  border-radius: 14px; padding: 10px 16px;
  z-index: 3; box-shadow: 0 8px 32px rgba(0,0,0,0.45);
  white-space: nowrap; cursor: default;
  transition: border-color 0.35s, box-shadow 0.35s, background 0.35s,
              transform 0.4s cubic-bezier(0.34,1.56,0.64,1);
}
.float-badge:hover {
  border-color: rgba(192,154,48,0.55);
  background: rgba(14,11,4,0.94);
  box-shadow: 0 12px 40px rgba(0,0,0,0.55), 0 0 24px rgba(192,154,48,0.18), inset 0 1px 0 rgba(192,154,48,0.12);
  transform: translateY(-5px) scale(1.05);
  animation-play-state: paused;
}
.float-badge:hover .fbadge-icon { transform: scale(1.2) rotate(-5deg); display: inline-block; }
.fbadge-icon { font-size: 20px; transition: transform 0.35s cubic-bezier(0.34,1.56,0.64,1); }
.float-badge-top {
  top: 28px; right: -28px;
  animation: badge-float-top 5s ease-in-out infinite; animation-delay: 0.8s;
}
.float-badge-bottom {
  bottom: 52px; left: -28px;
  animation: badge-float-bottom 5s ease-in-out infinite; animation-delay: 1.6s;
}
@keyframes badge-float-top    { 0%,100%{transform:translate(0,0)}  50%{transform:translate(4px,-8px)} }
@keyframes badge-float-bottom { 0%,100%{transform:translate(0,0)}  50%{transform:translate(-4px,6px)} }
.fbadge-text { display: flex; flex-direction: column; line-height: 1.2; }
.fbadge-val {
  font-size: 16px; font-weight: 800;
  background: linear-gradient(135deg, var(--gold), var(--gold-light));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
}
.fbadge-label { font-size: 11px; color: var(--gray-light); letter-spacing: 0.3px; }

.deco-ring {
  position: absolute; inset: -16px; border-radius: 28px;
  border: 1px dashed rgba(192,154,48,0.14); z-index: 0;
  animation: ring-rotate 20s linear infinite;
}
@keyframes ring-rotate { from{transform:rotate(0deg)} to{transform:rotate(360deg)} }

/* ── Scroll hint ──────────────────────────────────────── */
.scroll-hint {
  position: absolute; bottom: 32px; left: 50%;
  transform: translateX(-50%);
  display: flex; flex-direction: column; align-items: center; gap: 8px;
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
  .hero-inner { grid-template-columns: 1fr; text-align: center; padding-top: 110px; padding-bottom: 80px; }
  .hero-title { letter-spacing: -1px; }
  .hero-sub { margin: 0 auto 36px; max-width: 100%; }
  .hero-actions { justify-content: center; flex-direction: column; align-items: stretch; }
  .btn-primary, .btn-ghost { justify-content: center; }
  .hero-visual .photo-frame { display: none; }
  .hero-visual { order: -1; gap: 0; }
  .hero-visual .cert-badge { margin: 0 auto 28px; }
}
</style>
