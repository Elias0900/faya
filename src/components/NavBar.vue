<template>
  <nav :class="['navbar', { scrolled: isScrolled }]">
    <div class="container nav-inner">
      <a href="#hero" class="logo">
        <img :src="logoSrc" alt="Logo" class="logo-img" @error="onLogoError" />
        <div class="logo-text-group">
          <span class="logo-text logo-fallback">ELITE<span class="gold">COACH</span></span>
          <span class="logo-tagline">MAKE IT HAPPEN</span>
        </div>
      </a>
      <ul class="nav-links" :class="{ open: menuOpen }">
        <li><a href="#services" @click="menuOpen = false">Programmes</a></li>
        <li><a href="#stats" @click="menuOpen = false">Résultats</a></li>
        <li><a href="#testimonials" @click="menuOpen = false">Témoignages</a></li>
        <li><a href="#contact" @click="menuOpen = false" class="nav-cta">Commencer</a></li>
      </ul>
      <button class="burger" @click="menuOpen = !menuOpen" aria-label="Menu">
        <span :class="{ active: menuOpen }"></span>
        <span :class="{ active: menuOpen }"></span>
        <span :class="{ active: menuOpen }"></span>
      </button>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)

// Dépose ton logo dans public/ sous le nom logo.png (ou logo.svg)
const logoSrc = '/logo.png'

function onLogoError(e: Event) {
  const img = e.target as HTMLImageElement
  img.style.display = 'none'
  const fallback = img.nextElementSibling as HTMLElement
  if (fallback) fallback.style.display = 'inline'
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding: 20px 0;
  transition: all 0.4s ease;
}
.navbar.scrolled {
  background: rgba(8, 8, 8, 0.92);
  backdrop-filter: blur(20px);
  padding: 14px 0;
  border-bottom: 1px solid var(--border);
}
.nav-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
  font-weight: 800;
  font-size: 18px;
  letter-spacing: 2px;
  color: var(--white);
  transition: opacity 0.3s;
}
.logo:hover { opacity: 0.85; }

/* Image logo */
.logo-img {
  height: 75px;
  width: auto;
  object-fit: contain;
  display: block;
  transition: transform 0.35s cubic-bezier(0.34,1.56,0.64,1), filter 0.35s ease;
}
.logo:hover .logo-img {
  transform: scale(1.1);
  filter: drop-shadow(0 0 10px rgba(201,162,39,0.7)) drop-shadow(0 0 24px rgba(201,162,39,0.35));
}

/* Groupe texte à droite du logo image */
.logo-text-group {
  display: flex;
  flex-direction: column;
  gap: 1px;
}

/* Fallback texte — visible uniquement si logo absent */
.logo-fallback {
  display: none;
}

/* Tagline toujours visible */
.logo-tagline {
  font-size: 10px;
  font-weight: 700;
  letter-spacing: 3.5px;
  text-transform: uppercase;
  color: #ffffff;
  opacity: 0.85;
  line-height: 1;
}

.gold { color: var(--gold); }
.nav-links {
  display: flex;
  align-items: center;
  gap: 36px;
  list-style: none;
}
.nav-links a {
  text-decoration: none;
  color: var(--gray-light);
  font-size: 14px;
  font-weight: 500;
  letter-spacing: 0.5px;
  transition: color 0.3s;
}
.nav-links a:hover {
  color: var(--white);
}
.nav-cta {
  background: var(--gold) !important;
  color: #000 !important;
  padding: 10px 22px;
  border-radius: 8px;
  font-weight: 700 !important;
  transition: background 0.3s, transform 0.2s !important;
}
.nav-cta:hover {
  background: var(--gold-light) !important;
  transform: translateY(-1px);
}
.burger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
}
.burger span {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--white);
  border-radius: 2px;
  transition: all 0.3s ease;
}
.burger span.active:nth-child(1) { transform: rotate(45deg) translate(5px, 5px); }
.burger span.active:nth-child(2) { opacity: 0; }
.burger span.active:nth-child(3) { transform: rotate(-45deg) translate(5px, -5px); }

/* Tablet : liens condensés */
@media (max-width: 900px) and (min-width: 641px) {
  .nav-links { gap: 20px; }
  .nav-links a { font-size: 13px; }
  .nav-cta { padding: 8px 16px !important; }
}

/* Mobile : menu burger */
@media (max-width: 640px) {
  .burger { display: flex; }
  .nav-links {
    position: fixed;
    top: 0;
    right: -100%;
    width: 75%;
    height: 100vh;
    background: var(--bg-secondary);
    flex-direction: column;
    justify-content: center;
    gap: 36px;
    transition: right 0.4s ease;
    border-left: 1px solid var(--border);
    padding: 0 32px;
    z-index: 99;
  }
  .nav-links.open { right: 0; }
  .nav-links a { font-size: 18px; }
}
</style>
