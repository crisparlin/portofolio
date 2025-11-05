<template>
  <div id="app">
    <AppHeader :scrollToSection="scrollToSection" />
    <HeroSection :scrollToSection="scrollToSection" />
    <AboutSection />
    <ExperienceSection />
    <SkillsSection />
    <PortfolioSection />
    <ContactSection />
    <AppFooter :scrollToSection="scrollToSection" />
  </div>
</template>

<script setup>
// Import components
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import ContactSection from './components/ContactSection.vue'
import AppFooter from './components/AppFooter.vue'

// Scroll to section function
const scrollToSection = (sectionId) => {
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
}
</script>

<style>
/* Variables - Light Mode (Professional Tech Look) */
:root {
  --primary-color: #1E3A8A;      /* Navy Blue */
  --secondary-color: #14B8A6;     /* Teal */
  --accent-color: #F59E0B;        /* Amber */
  --background-color: #F9FAFB;    /* Light Gray */
  --surface-color: #FFFFFF;       /* White */
  --text-color: #111827;          /* Graphite */
  --text-secondary: #6B7280;      /* Gray for secondary text */
  --border-color: #E5E7EB;        /* Light border */
  --shadow: 0 4px 6px -1px rgba(30, 58, 138, 0.1), 0 2px 4px -1px rgba(30, 58, 138, 0.06);
  --shadow-lg: 0 20px 25px -5px rgba(30, 58, 138, 0.1), 0 10px 10px -5px rgba(30, 58, 138, 0.04);
  --gradient-start: #1E3A8A;
  --gradient-end: #14B8A6;
  --hero-gradient: linear-gradient(135deg, #1E3A8A 0%, #14B8A6 100%);
}

/* Dark Mode (Modern Engineer) */
@media (prefers-color-scheme: dark) {
  :root {
    --primary-color: #2563EB;      /* Cobalt */
    --secondary-color: #10B981;     /* Emerald */
    --accent-color: #F59E0B;        /* Amber */
    --background-color: #0F172A;    /* Deep Navy */
    --surface-color: #1E293B;       /* Slate */
    --text-color: #F1F5F9;          /* Off-white */
    --text-secondary: #94A3B8;      /* Light gray for secondary text */
    --border-color: #334155;        /* Dark border */
    --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3), 0 2px 4px -1px rgba(0, 0, 0, 0.2);
    --shadow-lg: 0 20px 25px -5px rgba(0, 0, 0, 0.3), 0 10px 10px -5px rgba(0, 0, 0, 0.2);
    --gradient-start: #2563EB;
    --gradient-end: #10B981;
    --hero-gradient: linear-gradient(135deg, #1E3A8A 0%, #2563EB 50%, #10B981 100%);
  }
}

/* Reset & Base */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  color: var(--text-color);
  line-height: 1.6;
  background-color: var(--background-color);
  transition: background-color 0.3s ease, color 0.3s ease;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Section Title Styles */
.section-title {
  text-align: center;
  font-size: 2.8rem;
  font-weight: 900;
  color: var(--text-color);
  margin-bottom: 60px;
  position: relative;
  padding-bottom: 20px;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 5px;
  background: linear-gradient(90deg, #1E3A8A 0%, #14B8A6 50%, #F59E0B 100%);
  border-radius: 3px;
  box-shadow: 0 3px 10px rgba(30, 58, 138, 0.3);
}

.section-title::before {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 50%;
  transform: translateX(-50%);
  width: 15px;
  height: 15px;
  background: #F59E0B;
  border-radius: 50%;
  box-shadow: 0 0 15px rgba(245, 158, 11, 0.6);
}

@media (prefers-color-scheme: dark) {
  .section-title::after {
    background: linear-gradient(90deg, #2563EB 0%, #10B981 50%, #F59E0B 100%);
    box-shadow: 0 3px 10px rgba(37, 99, 235, 0.4);
  }
}

@media (max-width: 640px) {
  .section-title {
    font-size: 2rem;
  }
}
</style>
