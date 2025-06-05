<template>
  <nav class="navbar">
    <div class="nav-container">
      <h1 class="logo">PORTOFOLIO</h1>
      <ul class="nav-menu">
        <li><a href="#Home" 
               :class="{ active: activeSection === 'Home' }"
               @click.prevent="scrollToSection('Home')">Home</a></li>
        <li><a href="#Education" 
               :class="{ active: activeSection === 'Education' }" 
               @click.prevent="scrollToSection('Education')">Education</a></li>
        <li><a href="#About" 
               :class="{ active: activeSection === 'About' }"
               @click.prevent="scrollToSection('About')">About</a></li>
        <li><a href="#Contact" 
               :class="{ active: activeSection === 'Contact' }"
               class="contact-button"
               @click.prevent="scrollToSection('Contact')">Contact</a></li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
// hahaha
import { ref, onMounted, onBeforeUnmount } from 'vue'

const activeSection = ref('Home')

function scrollToSection(id) {
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth' })
  }
}

// Fungsi untuk update activeSection berdasarkan scroll
function onScroll() {
  const sections = ['Home', 'Education', 'About', 'Contact']
  let current = activeSection.value

  for (const id of sections) {
    const el = document.getElementById(id)
    if (!el) continue
    const rect = el.getBoundingClientRect()
    // Jika top section sudah lewat navbar dan belum terlalu jauh ke atas
    if (rect.top <= 120 && rect.bottom > 120) {
      current = id
      break
    }
  }

  activeSection.value = current
}

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })
  onScroll() // cek saat pertama load
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', onScroll)
})
</script>

<style scoped>
.navbar {
  position: fixed; /* Agar navbar tetap di atas */
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  background-color: #1f1f1f;
  padding: 1rem 2rem;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  color: white;
  font-weight: bold;
  font-size: 1.2rem;
  letter-spacing: 1px;
}

.nav-menu {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 2rem;
  margin: 0;
  padding: 0;
}

.nav-menu a {
  color: #ccc;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
  cursor: pointer;
}

.nav-menu a:hover {
  color: #00d8ff;
}

.nav-menu a.active {
  color: #44f1e3;
  font-weight: 700;
}

.contact-button {
  background-color: #00bcd4;
  color: white !important;
  padding: 0.4em 1em;
  border-radius: 999px;
  font-weight: bold;
  transition: background-color 0.3s ease;
}

.contact-button:hover {
  background-color: #0097a7;
}

.contact-button.active {
  background-color: #44f1e3;
  color: #0e0e24 !important;
}
</style>
