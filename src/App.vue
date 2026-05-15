<template>
  <div>
    <NavBar />
    <HeroSection />
    <StatsSection />
    <ServicesSection />
    <TestimonialsSection />
    <ContactSection />
    <FooterSection />
  </div>
</template>

<script setup lang="ts">
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import StatsSection from './components/StatsSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import TestimonialsSection from './components/TestimonialsSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'

import { onMounted } from 'vue'

/* Easing easeInOutQuart — douce accélération + décélération */
function easeInOutQuart(t: number): number {
  return t < 0.5 ? 8 * t * t * t * t : 1 - Math.pow(-2 * t + 2, 4) / 2
}

function smoothScrollTo(targetY: number, duration = 950) {
  const startY = window.scrollY
  const distance = targetY - startY
  if (Math.abs(distance) < 2) return
  const startTime = performance.now()

  function step(now: number) {
    const progress = Math.min((now - startTime) / duration, 1)
    window.scrollTo(0, startY + distance * easeInOutQuart(progress))
    if (progress < 1) requestAnimationFrame(step)
  }
  requestAnimationFrame(step)
}

onMounted(() => {
  /* Scroll animé sur tous les liens ancre */
  document.addEventListener('click', (e) => {
    const anchor = (e.target as HTMLElement).closest('a[href^="#"]') as HTMLAnchorElement | null
    if (!anchor) return
    const id = anchor.getAttribute('href')
    if (!id || id === '#') return
    const target = document.querySelector(id) as HTMLElement | null
    if (!target) return
    e.preventDefault()
    const offset = target.getBoundingClientRect().top + window.scrollY
    smoothScrollTo(offset, 950)
  })

  /* Animations au scroll (IntersectionObserver) */
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) entry.target.classList.add('visible')
      })
    },
    { threshold: 0.12 }
  )
  document.querySelectorAll('.reveal, .reveal-left, .reveal-right').forEach((el) => {
    observer.observe(el)
  })
})
</script>
