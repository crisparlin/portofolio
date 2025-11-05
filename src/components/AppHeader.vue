<template>
  <header class="header" :class="{ 'header-scrolled': isScrolled }">
    <div class="container">
      <div class="header-content">
        <div class="logo">
          <h2>PORTOFOLIO</h2>
        </div>
        <nav class="nav">
          <a href="#home" @click.prevent="scrollTo('home')" class="nav-link">Home</a>
          <a href="#about" @click.prevent="scrollTo('about')" class="nav-link">About</a>
          <a href="#experience" @click.prevent="scrollTo('experience')" class="nav-link">Experience</a>
          <a href="#skills" @click.prevent="scrollTo('skills')" class="nav-link">Skills</a>
          <a href="#portfolio" @click.prevent="scrollTo('portfolio')" class="nav-link">Portfolio</a>
          <a href="#contact" @click.prevent="scrollTo('contact')" class="nav-link">Contact</a>
        </nav>
        <button class="mobile-menu-btn" @click="toggleMenu">
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
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
}

@media (prefers-color-scheme: dark) {
  .header {
    background: rgba(15, 23, 42, 0.95);
  }
}

.header-scrolled {
  box-shadow: var(--shadow);
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 0;
}

.logo h2 {
  color: var(--text-color);
  font-size: 1.5rem;
  margin-bottom: 2px;
}

.logo .subtitle {
  font-size: 0.85rem;
  color: var(--primary-color);
  font-weight: 500;
}

.nav {
  display: flex;
  gap: 30px;
}

.nav-link {
  color: var(--text-color);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
  cursor: pointer;
}

.nav-link:hover {
  color: var(--primary-color);
}

.mobile-menu-btn {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 10px;
}

.mobile-menu-btn span {
  width: 25px;
  height: 3px;
  background: var(--text-color);
  transition: all 0.3s ease;
}

.mobile-nav {
  display: none;
}

/* Responsive Design */
@media (max-width: 968px) {
  .nav {
    display: none;
  }

  .mobile-menu-btn {
    display: flex;
  }

  .mobile-nav {
    display: flex;
    flex-direction: column;
    gap: 15px;
    padding: 20px 0;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.3s ease;
  }

  .mobile-nav.active {
    max-height: 400px;
  }
}
</style>
