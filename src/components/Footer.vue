<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-brand">
          <h3>{{ name }}</h3>
          <p>{{ tagline }}</p>
          <div class="social-links">
            <a v-for="social in socialLinks" :key="social.name" :href="social.url" target="_blank" class="social-link">
              <i :class="social.icon"></i>
            </a>
          </div>
        </div>
        
        <div class="footer-links">
          <div class="link-group">
            <h4>Quick Links</h4>
            <ul>
              <li><a href="#home" @click="scrollTo('home')">Home</a></li>
              <li><a href="#about" @click="scrollTo('about')">About</a></li>
              <li><a href="#services" @click="scrollTo('services')">Services</a></li>
              <li><a href="#portfolio" @click="scrollTo('portfolio')">Portfolio</a></li>
              <li><a href="#contact" @click="scrollTo('contact')">Contact</a></li>
            </ul>
          </div>
          
          <div class="link-group">
            <h4>Services</h4>
            <ul>
              <li><a href="#services">Web Development</a></li>
              <li><a href="#services">Mobile Apps</a></li>
              <li><a href="#services">Backend Development</a></li>
              <li><a href="#services">Cloud Solutions</a></li>
              <li><a href="#services">IT Consulting</a></li>
            </ul>
          </div>
          
          <div class="link-group">
            <h4>Contact Info</h4>
            <ul class="contact-info">
              <li>
                <i class="fas fa-envelope"></i>
                <a href="mailto:your.email@example.com">your.email@example.com</a>
              </li>
              <li>
                <i class="fas fa-phone"></i>
                <a href="tel:+1234567890">+1 (234) 567-890</a>
              </li>
              <li>
                <i class="fas fa-map-marker-alt"></i>
                <span>Jakarta, Indonesia</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
      
      <div class="footer-bottom">
        <div class="footer-bottom-content">
          <p>&copy; {{ currentYear }} {{ name }}. All rights reserved.</p>
          <div class="footer-bottom-links">
            <a href="#privacy">Privacy Policy</a>
            <a href="#terms">Terms of Service</a>
            <a href="#sitemap">Sitemap</a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue'

defineProps({
  name: {
    type: String,
    default: 'Your Name'
  },
  tagline: {
    type: String,
    default: 'Full Stack Developer & IT Consultant'
  },
  socialLinks: {
    type: Array,
    default: () => [
      { name: 'GitHub', url: 'https://github.com', icon: 'fab fa-github' },
      { name: 'LinkedIn', url: 'https://linkedin.com', icon: 'fab fa-linkedin' },
      { name: 'Twitter', url: 'https://twitter.com', icon: 'fab fa-twitter' },
      { name: 'Instagram', url: 'https://instagram.com', icon: 'fab fa-instagram' }
    ]
  }
})

const currentYear = computed(() => new Date().getFullYear())

const scrollTo = (elementId) => {
  const element = document.getElementById(elementId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<style scoped>
.footer {
  background: #2c3e50;
  color: white;
  padding: 3rem 0 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 5%;
}

.footer-content {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 3rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid #34495e;
}

.footer-brand h3 {
  font-size: 1.8rem;
  margin-bottom: 1rem;
  color: #3498db;
}

.footer-brand p {
  font-size: 1.1rem;
  margin-bottom: 1.5rem;
  opacity: 0.8;
  line-height: 1.6;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 45px;
  height: 45px;
  background: #34495e;
  color: white;
  border-radius: 50%;
  text-decoration: none;
  transition: all 0.3s ease;
  font-size: 1.2rem;
}

.social-link:hover {
  background: #3498db;
  transform: translateY(-3px);
}

.footer-links {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.link-group h4 {
  font-size: 1.2rem;
  margin-bottom: 1rem;
  color: #3498db;
}

.link-group ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.link-group li {
  margin-bottom: 0.8rem;
}

.link-group a {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  transition: color 0.3s ease;
  cursor: pointer;
}

.link-group a:hover {
  color: #3498db;
}

.contact-info li {
  display: flex;
  align-items: center;
  gap: 0.8rem;
}

.contact-info i {
  color: #3498db;
  width: 16px;
}

.footer-bottom {
  padding: 1.5rem 0;
}

.footer-bottom-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.footer-bottom p {
  margin: 0;
  opacity: 0.7;
}

.footer-bottom-links {
  display: flex;
  gap: 2rem;
}

.footer-bottom-links a {
  color: rgba(255, 255, 255, 0.6);
  text-decoration: none;
  font-size: 0.9rem;
  transition: color 0.3s ease;
}

.footer-bottom-links a:hover {
  color: #3498db;
}

@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .footer-links {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
  
  .footer-bottom-content {
    flex-direction: column;
    text-align: center;
  }
  
  .footer-bottom-links {
    justify-content: center;
  }
}
</style>
