<template>
  <div class="main-container">
    <Navbar />

    <section class="home-section fade-in" id="Home">
      <div class="text-container">
        <h1 class="greeting">
          Hello, I'm <span class="highlight">Federick</span>,<br />
          frontend developer
        </h1>
        <p class="description">
          Former digital marketing specialist, seeking to spark development
          advancement with the force of collaboration, communication, and passion.
        </p>
        <a href="#Contact" class="cta-button">Let’s Connect </a>
      </div>
<div class="image-container">
  <div class="circle circle-outline"></div>
  <img src="/profile.jpg" alt="Profile Picture" class="profile-pic" />
  <div class="circle circle-blue"></div>
</div>

    </section>

    <section class="about-section fade-in" id="About">
      <h2 class="section-title">About Me</h2>
      <p class="section-text">
I'm a student at the Islamic University of Riau majoring in Informatics Engineering. I’m passionate about web development, especially using Vue.js.
      </p>
    </section>

    <section class="projects-section fade-in" id="Education">
      <h2 class="section-title">Academic History</h2>
      <div class="projects-grid">
        <div class="project-card">
          <h3>SD</h3>
          <p>I attended Muslimin Elementary School in Dumai.</p>
        </div>
        <div class="project-card">
          <h3>SMP</h3>
          <p>I attended YKPP Junior High School in Dumai.</p>
        </div>
        <div class="project-card">
          <h3>SMK</h3>
          <p>I attended Vocational High School 5 (SMK 5) in Dumai.</p>
        </div>
      </div>
    </section>

    <section class="contact-section fade-in" id="Contact">
      <h2 class="section-title">Contact</h2>
      <p class="section-text">
        Feel free to reach out to me via email at
        <a href="mailto:email@example.com">email@Federick</a> or connect with me on social media.
      </p>
    </section>
  </div>
</template>

<script setup>
import { onMounted, onBeforeUnmount } from 'vue'
import Navbar from './components/Navbar.vue'

let observer = null

onMounted(() => {
  observer = new IntersectionObserver(
    entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible')
        } else {
          entry.target.classList.remove('visible')
        }
      })
    },
    { threshold: 0.1 }
  )

  document.querySelectorAll('.fade-in').forEach(el => {
    observer.observe(el)
  })
})

onBeforeUnmount(() => {
  if (observer) observer.disconnect()
})
</script>

<style scoped>
html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #0e0e24;
  color: white;
}

.main-container {
  width: 100%;
}

section {
  scroll-margin-top: 100px; /* Sesuaikan dengan tinggi navbar */
  padding: 120px 20px;
  margin-bottom: 80px; /* Tambah jarak bawah supaya antar section tidak mepet */
}


/* Fade In Animation */
.fade-in {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.8s ease, transform 0.8s ease;
}
.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}

.home-section {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 80px 100px;
  min-height: 100vh;
  background-color: #0e0e24;
}

.text-container {
  max-width: 600px;
}

.greeting {
  font-size: 2.8rem;
  font-weight: bold;
  margin-bottom: 20px;
  line-height: 1.2;
}

.highlight {
  color: #44f1e3;
}

.description {
  font-size: 1rem;
  margin-bottom: 30px;
  color: #ccc;
}

.cta-button {
  padding: 12px 28px;
  background: linear-gradient(90deg, #8f44fd, #44f1e3);
  border-radius: 25px;
  color: white;
  text-decoration: none;
  font-weight: bold;
  transition: 0.3s;
}

.cta-button:hover {
  opacity: 0.8;
}

.image-container {
  position: relative;
  width: 250px;
  height: 250px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.profile-pic {
  width: 160px;
  height: 160px;
  border-radius: 50%;
  border: 4px solid #fff;
  position: absolute;
  z-index: 2;
  object-fit: cover;
}

.circle-outline {
  width: 250px;
  height: 250px;
  border: 2px solid #444;
  border-radius: 50%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
}

.circle-blue {
  width: 60px;
  height: 60px;
  background-color: #44f1e3;
  border-radius: 50%;
  position: absolute;
  bottom: -10px;
  right: -10px;
  z-index: 3;
}


.circle-outline {
  width: 250px;
  height: 250px;
  border: 1px solid #444;
  top: -30px;
  left: -50px;
}

.section-title {
  font-size: 2rem;
  color: #44f1e3;
  text-align: center;
  margin-bottom: 20px;
}

.section-text {
  max-width: 700px;
  margin: 0 auto 60px;
  text-align: center;
  color: #ccc;
}

.projects-grid {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 20px;
  padding: 0 100px;
}

.project-card {
  background-color: #1a1a3a;
  border-radius: 16px;
  padding: 20px;
  width: 280px;
  color: #eee;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s ease;
}

.project-card:hover {
  transform: translateY(-5px);
}

.contact-section a {
  color: #44f1e3;
  text-decoration: none;
}

.contact-section a:hover {
  text-decoration: underline;
}
</style>
