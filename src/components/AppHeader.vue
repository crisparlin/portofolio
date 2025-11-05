<template>
  <header class="header" :class="{ 'header-scrolled': isScrolled }">
    <div class="container">
      <div class="header-content">
        <div class="logo">
          <img src="../assets/logo_cp.png" alt="CP Logo" class="logo-image">
          <span class="logo-full">PORTFOLIO</span>
        </div>
        <nav class="nav">
          <a href="#home" @click.prevent="scrollTo('home')" class="nav-link">Home</a>
          <a href="#about" @click.prevent="scrollTo('about')" class="nav-link">About</a>
          <a href="#experience" @click.prevent="scrollTo('experience')" class="nav-link">Experience</a>
          <a href="#skills" @click.prevent="scrollTo('skills')" class="nav-link">Skills</a>
          <a href="#portfolio" @click.prevent="scrollTo('portfolio')" class="nav-link">Portfolio</a>
          <a href="#contact" @click.prevent="scrollTo('contact')" class="nav-link">Contact</a>
        </nav>
        <button class="mobile-menu-btn" @click="toggleMenu" :class="{ 'active': mobileMenuOpen }">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
      <div class="mobile-nav" :class="{ 'active': mobileMenuOpen }">
        <a href="#home" @click="scrollTo('home')" class="nav-link">Home</a>
        <a href="#about" @click="scrollTo('about')" class="nav-link">About</a>
        <a href="#experience" @click="scrollTo('experience')" class="nav-link">Experience</a>
        <a href="#skills" @click="scrollTo('skills')" class="nav-link">Skills</a>
        <a href="#portfolio" @click="scrollTo('portfolio')" class="nav-link">Portfolio</a>
        <a href="#contact" @click="scrollTo('contact')" class="nav-link">Contact</a>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// Props
defineProps({
  scrollToSection: {
    type: Function,
    required: true
  }
})

// State
const isScrolled = ref(false)
const mobileMenuOpen = ref(false)

// Methods
const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const scrollTo = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    const offset = 80
    const elementPosition = element.getBoundingClientRect().top
    const offsetPosition = elementPosition + window.pageYOffset - offset

    window.scrollTo({
      top: offsetPosition,
      behavior: 'smooth'
    })
  }
  mobileMenuOpen.value = false
}

// Lifecycle
onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
/* Header */
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(255, 255, 255, 0.98);
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
  border-bottom: 1px solid transparent;
}

@media (prefers-color-scheme: dark) {
  .header {
    background: rgba(15, 23, 42, 0.98);
  }
}

.header-scrolled {
  box-shadow: var(--shadow);
  border-bottom: 1px solid var(--border-color);
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 18px 0;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
}

.logo-image {
  height: 45px;
  width: auto;
  object-fit: contain;
  transition: transform 0.3s ease;
}

.logo-image:hover {
  transform: scale(1.05);
}

.logo-full {
  color: var(--text-color);
  font-size: 1.5rem;
  font-weight: 800;
}

.nav {
  display: flex;
  gap: 30px;
  align-items: center;
}

.nav-link {
  color: var(--text-color);
  text-decoration: none;
  font-weight: 600;
  font-size: 0.95rem;
  transition: all 0.3s ease;
  cursor: pointer;
  position: relative;
  padding: 8px 0;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--primary-color);
  transition: width 0.3s ease;
}

.nav-link:hover {
  color: var(--primary-color);
}

.nav-link:hover::after {
  width: 100%;
}

.mobile-menu-btn {
  display: none;
  flex-direction: column;
  gap: 6px;
  background: none;
  border: 2px solid var(--border-color);
  cursor: pointer;
  padding: 12px;
  border-radius: 8px;
  transition: all 0.3s ease;
  width: 50px;
  height: 50px;
  justify-content: center;
  align-items: center;
}

.mobile-menu-btn:hover {
  border-color: var(--primary-color);
  background: rgba(30, 58, 138, 0.05);
}

.mobile-menu-btn span {
  width: 24px;
  height: 3px;
  background: var(--text-color);
  transition: all 0.3s ease;
  border-radius: 2px;
}

.mobile-menu-btn.active span:nth-child(1) {
  transform: rotate(45deg) translateY(9px);
}

.mobile-menu-btn.active span:nth-child(2) {
  opacity: 0;
}

.mobile-menu-btn.active span:nth-child(3) {
  transform: rotate(-45deg) translateY(-9px);
}

.mobile-nav {
  display: none;
}

/* Responsive Design */
@media (max-width: 968px) {
  .nav {
    display: none;
  }

  .logo-full {
    display: none;
  }

  .mobile-menu-btn {
    display: flex;
  }

  .mobile-nav {
    display: flex;
    flex-direction: column;
    gap: 0;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.4s ease;
    background: var(--surface-color);
    border-radius: 0 0 12px 12px;
  }

  .mobile-nav.active {
    max-height: 400px;
    border-top: 1px solid var(--border-color);
    padding: 10px 0;
  }

  .mobile-nav .nav-link {
    padding: 15px 20px;
    border-radius: 8px;
    margin: 0 10px;
    transition: all 0.3s ease;
  }

  .mobile-nav .nav-link:hover {
    background: rgba(30, 58, 138, 0.05);
  }

  .mobile-nav .nav-link::after {
    display: none;
  }
}

@media (max-width: 640px) {
  .header-content {
    padding: 15px 0;
  }

  .logo-image {
    height: 38px;
  }

  .mobile-menu-btn {
    width: 45px;
    height: 45px;
    padding: 10px;
  }

  .mobile-menu-btn span {
    width: 22px;
  }
}
</style>
