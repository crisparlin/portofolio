<template>
  <header class="header">
    <nav class="nav">
      <div class="nav-brand">
        <h2>{{ name }}</h2>
      </div>
      <ul class="nav-links">
        <li><a href="#home" @click="scrollTo('home')">Home</a></li>
        <li><a href="#about" @click="scrollTo('about')">About</a></li>
        <li><a href="#services" @click="scrollTo('services')">Services</a></li>
        <li><a href="#portfolio" @click="scrollTo('portfolio')">Portfolio</a></li>
        <li><a href="#contact" @click="scrollTo('contact')">Contact</a></li>
      </ul>
      <div class="mobile-menu" @click="toggleMobileMenu">
        <span :class="{ active: mobileMenuOpen }"></span>
        <span :class="{ active: mobileMenuOpen }"></span>
        <span :class="{ active: mobileMenuOpen }"></span>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { ref } from 'vue'

defineProps({
  name: {
    type: String,
    default: 'Your Name'
  }
})

const mobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const scrollTo = (elementId) => {
  const element = document.getElementById(elementId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
  mobileMenuOpen.value = false
}
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background: rgba(255, 255, 255, 0.98);
  backdrop-filter: blur(20px);
  box-shadow: 0 2px 20px rgba(27, 60, 83, 0.1);
  z-index: 1000;
  transition: all 0.3s ease;
  border-bottom: 1px solid rgba(69, 104, 130, 0.1);
}

.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 5%;
  max-width: 1200px;
  margin: 0 auto;
}

.nav-brand h2 {
  color: #1B3C53;
  font-weight: 700;
  font-size: 1.5rem;
  margin: 0;
}

.nav-links {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 2rem;
}

.nav-links a {
  text-decoration: none;
  color: #456882;
  font-weight: 500;
  transition: color 0.3s ease;
  cursor: pointer;
  position: relative;
}

.nav-links a:hover {
  color: #1B3C53;
}

.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 0;
  height: 2px;
  background: #D2C1B6;
  transition: width 0.3s ease;
}

.nav-links a:hover::after {
  width: 100%;
}

.mobile-menu {
  display: none;
  flex-direction: column;
  cursor: pointer;
  gap: 4px;
}

.mobile-menu span {
  width: 25px;
  height: 3px;
  background: #456882;
  transition: all 0.3s ease;
}

.mobile-menu span.active:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.mobile-menu span.active:nth-child(2) {
  opacity: 0;
}

.mobile-menu span.active:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -6px);
}

@media (max-width: 768px) {
  .nav-links {
    display: none;
  }
  
  .mobile-menu {
    display: flex;
  }
}
</style>
