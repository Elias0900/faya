<template>
  <footer class="footer">
    <div class="container footer-inner">
      <div class="footer-brand">
        <span class="logo-text">ELITE<span class="gold">COACH</span></span>
        <p>Coaching basketball premium en Bretagne.<br />Transforme ta passion en excellence.</p>
      </div>
      <div class="footer-links">
        <a href="#services">Programmes</a>
        <a href="#stats">Résultats</a>
        <a href="#testimonials">Témoignages</a>
        <a href="#contact">Contact</a>
      </div>
      <div class="footer-bottom">
        <span>© {{ year }} EliteCoach · Bretagne</span>
        <span>Fait avec 🏀 en Bretagne</span>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
const year = new Date().getFullYear()
</script>

<style scoped>
.footer {
  border-top: 1px solid var(--border);
  padding: 60px 0 32px;
}
.footer-inner {
  display: flex;
  flex-direction: column;
  gap: 40px;
}
.footer-brand p {
  color: var(--gray-light);
  font-size: 14px;
  line-height: 1.6;
  margin-top: 10px;
}
.logo-text {
  font-weight: 900;
  font-size: 20px;
  letter-spacing: 2px;
  color: var(--white);
}
.gold { color: var(--gold); }
.footer-links {
  display: flex;
  gap: 32px;
  flex-wrap: wrap;
}
.footer-links a {
  color: var(--gray-light);
  text-decoration: none;
  font-size: 14px;
  transition: color 0.3s;
}
.footer-links a:hover {
  color: var(--gold);
}
.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 24px;
  border-top: 1px solid var(--border);
  font-size: 13px;
  color: var(--gray-mid);
  flex-wrap: wrap;
  gap: 12px;
}

@media (max-width: 640px) {
  .footer { padding: 48px 0 28px; }
  .footer-inner { gap: 28px; }
  .footer-links { gap: 20px; }
  .footer-bottom { flex-direction: column; align-items: flex-start; gap: 8px; }
}
</style>
