<template>
  <footer class="footer">
    <div class="container">
      <!-- Main Footer Content -->
      <div class="footer-main">
        <div class="footer-brand">
          <h3>Cris Parlindungan Panjaitan</h3>
          <p class="tagline">Team Leader & Full-Stack Developer</p>
          <p class="description">Building innovative ERP systems and enterprise applications</p>
        </div>
        
        <div class="footer-links">
          <div class="links-group">
            <h4>Navigate</h4>
            <ul>
              <li><a href="#home" @click.prevent="scrollTo('home')">Home</a></li>
              <li><a href="#about" @click.prevent="scrollTo('about')">About</a></li>
              <li><a href="#experience" @click.prevent="scrollTo('experience')">Experience</a></li>
              <li><a href="#skills" @click.prevent="scrollTo('skills')">Skills</a></li>
              <li><a href="#portfolio" @click.prevent="scrollTo('portfolio')">Portfolio</a></li>
              <li><a href="#contact" @click.prevent="scrollTo('contact')">Contact</a></li>
            </ul>
          </div>
          
          <div class="links-group">
            <h4>Connect</h4>
            <div class="contact-info">
              <a href="mailto:cristparlindungan@gmail.com" class="contact-link">
                <i class="fas fa-envelope"></i>
                <span>cristparlindungan@gmail.com</span>
              </a>
              <a href="https://www.linkedin.com/in/cris-parlindungan-96650a1bb/" target="_blank" class="contact-link">
                <i class="fab fa-linkedin-in"></i>
                <span>LinkedIn Profile</span>
              </a>
              <div class="contact-link">
                <i class="fas fa-map-marker-alt"></i>
                <span>Depok, Indonesia</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Footer Bottom -->
      <div class="footer-bottom">
        <p>&copy; {{ currentYear }} Cris Parlindungan Panjaitan. All rights reserved.</p>
        <div class="footer-social">
          <a href="https://www.linkedin.com/in/cris-parlindungan-96650a1bb/" target="_blank" class="social-icon" title="LinkedIn">
            <i class="fab fa-linkedin-in"></i>
          </a>
          <a href="https://github.com" target="_blank" class="social-icon" title="GitHub">
            <i class="fab fa-github"></i>
          </a>
          <a href="https://twitter.com" target="_blank" class="social-icon" title="Twitter">
            <i class="fab fa-twitter"></i>
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue'

defineProps({
  scrollToSection: {
    type: Function,
    required: true
  }
})

const currentYear = computed(() => new Date().getFullYear())

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
}
</script>

<style scoped>
.footer {
  background: linear-gradient(135deg, #0a0e27 0%, #1a1f3a 100%);
  color: white;
  padding: 60px 0 0;
  position: relative;
  overflow: hidden;
}

.footer::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(100, 255, 218, 0.5), transparent);
}

/* Main Footer */
.footer-main {
  display: grid;
  grid-template-columns: 1.5fr 1fr;
  gap: 60px;
  padding-bottom: 40px;
}

.footer-brand h3 {
  font-size: 1.8em;
  color: white;
  margin-bottom: 12px;
  font-weight: 700;
  background: linear-gradient(135deg, #fff, #e0e7ff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.tagline {
  color: #64ffda;
  font-size: 1.05em;
  font-weight: 600;
  margin-bottom: 10px;
}

.description {
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.7;
  font-size: 0.95em;
  max-width: 400px;
}

/* Footer Links */
.footer-links {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 40px;
}

.links-group h4 {
  color: #64ffda;
  font-size: 1.1em;
  margin-bottom: 20px;
  font-weight: 600;
  letter-spacing: 0.5px;
}

.links-group ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.links-group ul li {
  margin-bottom: 12px;
}

.links-group ul li a {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  transition: all 0.3s ease;
  cursor: pointer;
  font-size: 0.95em;
  display: inline-block;
  position: relative;
}

.links-group ul li a::before {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 2px;
  background: #64ffda;
  transition: width 0.3s ease;
}

.links-group ul li a:hover {
  color: #64ffda;
  transform: translateX(5px);
}

.links-group ul li a:hover::before {
  width: 100%;
}

/* Contact Info */
.contact-info {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.contact-link {
  display: flex;
  align-items: center;
  gap: 12px;
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  transition: all 0.3s ease;
  font-size: 0.95em;
}

.contact-link i {
  width: 20px;
  color: #64ffda;
  font-size: 1em;
}

.contact-link:hover {
  color: #64ffda;
  transform: translateX(3px);
}

/* Footer Bottom */
.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 25px 0;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  margin-top: 0;
}

.footer-bottom p {
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.9em;
  margin: 0;
}

.footer-social {
  display: flex;
  gap: 12px;
}

.social-icon {
  width: 38px;
  height: 38px;
  border-radius: 8px;
  background: rgba(100, 255, 218, 0.1);
  border: 1px solid rgba(100, 255, 218, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #64ffda;
  font-size: 1em;
  transition: all 0.3s ease;
  text-decoration: none;
}

.social-icon:hover {
  background: #64ffda;
  border-color: #64ffda;
  color: #0a0e27;
  transform: translateY(-3px);
}

/* Responsive Design */
@media (max-width: 968px) {
  .footer {
    padding: 40px 0 0;
  }

  .footer-main {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .footer-links {
    grid-template-columns: 1fr;
    gap: 30px;
  }

  .footer-bottom {
    flex-direction: column;
    gap: 20px;
    text-align: center;
    padding: 30px 0 25px;
  }

  .footer-social {
    justify-content: center;
  }
}

@media (max-width: 640px) {
  .footer-brand h3 {
    font-size: 1.5em;
  }

  .tagline {
    font-size: 1em;
  }

  .description {
    font-size: 0.9em;
  }

  .links-group h4 {
    font-size: 1em;
  }

  .links-group ul li a,
  .contact-link {
    font-size: 0.9em;
  }

  .social-icon {
    width: 36px;
    height: 36px;
    font-size: 0.95em;
  }
}
</style>
