<script setup>
import About from './components/About.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import Portfolio from './components/Portfolio.vue'
import Services from './components/Services.vue'

// Portfolio data - customize these according to your profile
const personalInfo = {
  name: 'IT Solutions Pro',
  title: 'Enterprise IT Solutions & Digital Transformation Expert',
  description: 'I help businesses leverage cutting-edge technology to increase efficiency, reduce operational costs by 40%, and accelerate digital growth. Specialized in scalable web applications, cloud infrastructure, and strategic IT consulting.',
  profileImage: 'https://via.placeholder.com/300x300/1B3C53/D2C1B6?text=IT+Expert',
  socialLinks: [
    { name: 'LinkedIn', url: 'https://linkedin.com/in/yourprofile', icon: 'fab fa-linkedin' },
    { name: 'GitHub', url: 'https://github.com/crisparlin', icon: 'fab fa-github' },
    { name: 'Email', url: 'mailto:contact@example.com', icon: 'fas fa-envelope' },
    { name: 'Phone', url: 'tel:+1234567890', icon: 'fas fa-phone' }
  ]
}
</script>

<template>
  <div id="app">
    <Header :name="personalInfo.name" />
    <Hero :name="personalInfo.name" :title="personalInfo.title" :description="personalInfo.description"
      :profile-image="personalInfo.profileImage" :social-links="personalInfo.socialLinks" />
    <About />
    <Services />
    <Portfolio />
    <Contact />
    <Footer :name="personalInfo.name" :tagline="personalInfo.title" :social-links="personalInfo.socialLinks" />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Open Sans', 'Helvetica Neue', sans-serif;
  line-height: 1.6;
  color: #333;
  scroll-behavior: smooth;
}

#app {
  min-height: 100vh;
}

/* Utility classes */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 5%;
}

/* Smooth scrolling for all browsers */
html {
  scroll-behavior: smooth;
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
}

::-webkit-scrollbar-thumb {
  background: #3498db;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #2980b9;
}

/* Loading animation for images */
img {
  max-width: 100%;
  height: auto;
  display: block;
}

/* Form focus styles */
input:focus,
textarea:focus,
select:focus {
  outline: 2px solid #3498db;
  outline-offset: 2px;
}

/* Button base styles */
button {
  font-family: inherit;
  cursor: pointer;
}

/* Link base styles */
a {
  color: inherit;
  text-decoration: none;
}

/* Responsive typography */
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }
}

/* Print styles */
@media print {
  * {
    background: transparent !important;
    color: black !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }

  a,
  a:visited {
    text-decoration: underline;
  }

  img {
    max-width: 100% !important;
  }

  .no-print {
    display: none !important;
  }
}
</style>
