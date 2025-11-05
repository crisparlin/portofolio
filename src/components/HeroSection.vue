<template>
    <section id="home" class="hero">
        <div class="hero-background-overlay"></div>
        <div class="container">
            <div class="hero-content">
                <div class="hero-text">
                    <div class="hero-badge">
                        <i class="fas fa-code"></i> Available for Freelance & Full-time
                    </div>
                    <h1 class="hero-title animate-fade-in">
                        <span class="highlight">Cris Parlindungan Panjaitan</span>
                    </h1>
                    <h2 class="hero-subtitle animate-fade-in-delay">Tech Lead Software Engineer</h2>

                    <div class="hero-stats">
                        <div class="stat-item">
                            <strong>8+</strong>
                            <span>Years Exp</span>
                        </div>
                        <div class="stat-item">
                            <strong>10+</strong>
                            <span>Projects</span>
                        </div>
                    </div>
                    <div class="hero-buttons animate-fade-in-delay-3">
                        <a href="#contact" @click.prevent="scrollToSection('contact')" class="btn btn-primary">
                            <i class="fas fa-paper-plane"></i> Get In Touch
                        </a>
                        <a href="#portfolio" @click.prevent="scrollToSection('portfolio')" class="btn btn-secondary">
                            <i class="fas fa-briefcase"></i> View My Work
                        </a>
                    </div>
                    <div class="hero-social animate-fade-in-delay-4">
                        <a href="https://www.linkedin.com/in/cris-parlindungan-96650a1bb/" target="_blank"
                            class="social-link" aria-label="LinkedIn">
                            <i class="fab fa-linkedin"></i>
                        </a>
                        <a href="mailto:cristparlindungan@gmail.com" class="social-link" aria-label="Email">
                            <i class="fas fa-envelope"></i>
                        </a>
                    </div>
                </div>
                <div class="hero-image animate-slide-in">
                    <div class="image-container">
                        <div class="image-placeholder">
                            <i class="fas fa-user-tie"></i>
                        </div>

                        <!-- Dynamic Tech Badges -->
                        <div v-for="badge in techBadges" :key="badge.text"
                            :class="['floating-badge', `badge-${badge.type}`, badge.class]">
                            <i :class="badge.icon"></i>
                            <span>{{ badge.text }}</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="scroll-indicator">
            <span>Scroll Down</span>
            <i class="fas fa-chevron-down"></i>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'

defineProps({
  scrollToSection: {
    type: Function,
    required: true
  }
})

// Tech badges data for easier maintenance
const techBadges = ref([
  // Main expertise
  { icon: 'fas fa-laptop-code', text: 'Full-Stack Dev', type: 'main', class: 'badge-1' },
  { icon: 'fas fa-users', text: 'Tech Lead', type: 'main', class: 'badge-2' },
  
  // Frontend technologies
  { icon: 'fab fa-vuejs', text: 'Vue.js', type: 'tech', class: 'badge-3' },
  { icon: 'fab fa-react', text: 'React Native', type: 'tech', class: 'badge-4' },
  
  // Backend technologies
  { icon: 'fas fa-code', text: '.NET', type: 'tech', class: 'badge-5' },
  { icon: 'fab fa-java', text: 'Spring Boot', type: 'tech', class: 'badge-6' },
  
  // Mobile
  { icon: 'fas fa-mobile-alt', text: 'Flutter', type: 'tech', class: 'badge-7' },
  
  // Databases
  { icon: 'fas fa-database', text: 'PostgreSQL', type: 'db', class: 'badge-8' },
  { icon: 'fas fa-database', text: 'SQL Server', type: 'db', class: 'badge-9' }
])
</script>

<style scoped>
/* Hero Section */
.hero {
  padding: 150px 0 80px;
  background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #334155 100%);
  color: white;
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.hero-background-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(circle at 20% 50%, rgba(59, 130, 246, 0.2) 0%, transparent 50%),
    radial-gradient(circle at 80% 80%, rgba(16, 185, 129, 0.2) 0%, transparent 50%);
  pointer-events: none;
}

.hero .container {
  position: relative;
  z-index: 1;
}

.hero-content {
  display: grid;
  grid-template-columns: 1.5fr 1fr;
  gap: 60px;
  align-items: center;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: linear-gradient(135deg, #14B8A6 0%, #0D9488 100%);
  padding: 12px 24px;
  border-radius: 50px;
  font-size: 1rem;
  font-weight: 700;
  margin-bottom: 25px;
  border: 2px solid rgba(255, 255, 255, 0.3);
  box-shadow: 0 8px 24px rgba(20, 184, 166, 0.6);
  animation: pulse 2s infinite;
}

.hero-badge i {
  color: white;
  font-size: 1.2rem;
}

.hero-title {
  font-size: 4rem;
  margin-bottom: 15px;
  line-height: 1.2;
  font-weight: 900;
  color: #ffffff;
  text-shadow: 3px 6px 12px rgba(0, 0, 0, 0.6);
}

.highlight {
  color: #FCD34D;
  text-shadow: 0 0 40px rgba(252, 211, 77, 0.9), 0 0 60px rgba(245, 158, 11, 0.7);
  animation: glow 2s ease-in-out infinite alternate;
}

@keyframes glow {
  from {
    text-shadow: 0 0 30px rgba(252, 211, 77, 0.8), 0 0 50px rgba(245, 158, 11, 0.6), 3px 6px 12px rgba(0, 0, 0, 0.6);
  }
  to {
    text-shadow: 0 0 50px rgba(252, 211, 77, 1), 0 0 80px rgba(245, 158, 11, 0.8), 3px 6px 12px rgba(0, 0, 0, 0.6);
  }
}

.hero-subtitle {
  font-size: 2.2rem;
  margin-bottom: 25px;
  color: #14B8A6;
  font-weight: 700;
  text-shadow: 2px 4px 8px rgba(0, 0, 0, 0.6);
}

.hero-description {
  font-size: 1.25rem;
  margin-bottom: 30px;
  line-height: 1.8;
  color: #e2e8f0;
  font-weight: 400;
  text-shadow: 2px 3px 6px rgba(0, 0, 0, 0.5);
}

.hero-stats {
  display: flex;
  gap: 30px;
  margin-bottom: 30px;
}

.stat-item {
  display: flex;
  flex-direction: column;
  padding: 20px 30px;
  background: rgba(20, 184, 166, 0.2);
  backdrop-filter: blur(15px);
  border-radius: 16px;
  border: 2px solid rgba(20, 184, 166, 0.5);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
}

.stat-item strong {
  font-size: 2.5rem;
  font-weight: 900;
  color: #FCD34D;
  text-shadow: 0 0 20px rgba(252, 211, 77, 0.8), 2px 3px 6px rgba(0, 0, 0, 0.5);
  margin-bottom: 4px;
}

.stat-item span {
  font-size: 1rem;
  color: #e2e8f0;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  text-shadow: 1px 2px 4px rgba(0, 0, 0, 0.4);
}

.hero-buttons {
  display: flex;
  gap: 15px;
  margin-bottom: 30px;
  flex-wrap: wrap;
}

.btn {
  padding: 18px 40px;
  border-radius: 12px;
  text-decoration: none;
  font-weight: 700;
  transition: all 0.3s ease;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  border: none;
  cursor: pointer;
  font-size: 1.15rem;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.5);
  text-shadow: 1px 2px 4px rgba(0, 0, 0, 0.3);
}

.btn-primary {
  background: linear-gradient(135deg, #FCD34D 0%, #F59E0B 100%);
  color: #1e293b;
  font-weight: 800;
}

.btn-primary:hover {
  transform: translateY(-3px) scale(1.05);
  box-shadow: 0 12px 35px rgba(252, 211, 77, 0.6);
  background: linear-gradient(135deg, #FDE68A 0%, #FCD34D 100%);
}

.btn-secondary {
  background: rgba(20, 184, 166, 0.2);
  color: #14B8A6;
  border: 3px solid #14B8A6;
  backdrop-filter: blur(10px);
  font-weight: 800;
}

.btn-secondary:hover {
  background: #14B8A6;
  color: white;
  transform: translateY(-3px) scale(1.05);
  box-shadow: 0 12px 35px rgba(20, 184, 166, 0.6);
}

.hero-social {
  display: flex;
  gap: 15px;
}

.social-link {
  width: 54px;
  height: 54px;
  border-radius: 50%;
  background: rgba(20, 184, 166, 0.2);
  backdrop-filter: blur(10px);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #14B8A6;
  font-size: 1.4rem;
  transition: all 0.3s ease;
  border: 2px solid rgba(20, 184, 166, 0.5);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.4);
}

.social-link:hover {
  background: #14B8A6;
  color: white;
  transform: translateY(-5px) scale(1.1);
  box-shadow: 0 10px 25px rgba(20, 184, 166, 0.6);
}

.hero-image {
  display: flex;
  justify-content: center;
  position: relative;
}

.image-container {
  position: relative;
  width: 450px;
  height: 450px;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Animated glow ring */
.image-container::before {
  content: '';
  position: absolute;
  width: 380px;
  height: 380px;
  border-radius: 50%;
  border: 3px solid transparent;
  background: linear-gradient(135deg, #14B8A6, #2563EB, #F59E0B, #14B8A6) border-box;
  -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
  animation: rotate-border 8s linear infinite;
  opacity: 0.4;
  z-index: 0;
}

@keyframes rotate-border {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.image-placeholder {
  width: 350px;
  height: 350px;
  border-radius: 50%;
  background: linear-gradient(135deg, rgba(20, 184, 166, 0.2) 0%, rgba(37, 99, 235, 0.2) 100%);
  backdrop-filter: blur(20px);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 140px;
  color: rgba(255, 255, 255, 0.9);
  border: 5px solid rgba(255, 255, 255, 0.3);
  box-shadow: 
    0 20px 60px rgba(0, 0, 0, 0.3),
    inset 0 0 50px rgba(255, 255, 255, 0.1),
    0 0 100px rgba(20, 184, 166, 0.2);
  animation: float 6s ease-in-out infinite;
  position: relative;
  z-index: 1;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

.floating-badge {
  position: absolute;
  padding: 12px 20px;
  border-radius: 50px;
  display: flex;
  align-items: center;
  gap: 8px;
  font-weight: 700;
  font-size: 0.9rem;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
  animation: float-badge 4s ease-in-out infinite;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
  white-space: nowrap;
}

.floating-badge:hover {
  transform: scale(1.1) translateY(-5px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.6);
  z-index: 10;
}

.floating-badge i {
  font-size: 1.2rem;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.2));
}

/* Main Expertise Badges - Larger and More Prominent */
.badge-main {
  background: linear-gradient(135deg, #FCD34D 0%, #F59E0B 100%);
  color: #1e293b;
  border: 3px solid rgba(255, 255, 255, 0.8);
  padding: 14px 26px;
  font-size: 1rem;
}

.badge-main i {
  color: #1e293b;
  font-size: 1.4rem;
}

/* Tech Stack Badges - Blue/Teal Theme */
.badge-tech {
  background: linear-gradient(135deg, rgba(30, 58, 138, 0.95) 0%, rgba(37, 99, 235, 0.95) 100%);
  color: white;
  border: 2px solid rgba(20, 184, 166, 0.6);
  font-size: 0.85rem;
  padding: 10px 18px;
}

.badge-tech i {
  color: #14B8A6;
}

/* Database Badges - Green Theme */
.badge-db {
  background: linear-gradient(135deg, rgba(20, 184, 166, 0.95) 0%, rgba(16, 185, 129, 0.95) 100%);
  color: white;
  border: 2px solid rgba(252, 211, 77, 0.6);
  font-size: 0.85rem;
  padding: 10px 18px;
}

.badge-db i {
  color: #FCD34D;
}

/* Badge Positions - Orbiting around the center */
.badge-1 {
  top: 5%;
  right: -8%;
  animation-delay: 0s;
}

.badge-2 {
  bottom: 35%;
  left: -12%;
  animation-delay: 0.5s;
}

.badge-3 {
  top: 15%;
  left: -10%;
  animation-delay: 1s;
}

.badge-4 {
  bottom: 8%;
  right: -5%;
  animation-delay: 1.5s;
}

.badge-5 {
  top: 35%;
  right: -12%;
  animation-delay: 2s;
}

.badge-6 {
  bottom: 15%;
  left: -8%;
  animation-delay: 2.5s;
}

.badge-7 {
  top: 50%;
  right: -15%;
  animation-delay: 3s;
}

.badge-8 {
  bottom: 50%;
  left: -13%;
  animation-delay: 3.5s;
}

.badge-9 {
  top: 70%;
  right: -10%;
  animation-delay: 4s;
}

@keyframes float-badge {
  0%, 100% {
    transform: translateY(0px) translateX(0px);
  }
  25% {
    transform: translateY(-8px) translateX(4px);
  }
  50% {
    transform: translateY(-15px) translateX(-2px);
  }
  75% {
    transform: translateY(-8px) translateX(3px);
  }
}

.scroll-indicator {
  position: absolute;
  bottom: 30px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  color: #e2e8f0;
  font-weight: 700;
  font-size: 1.05rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  animation: bounce-vertical 2s ease-in-out infinite;
}

.scroll-indicator i {
  font-size: 1.6rem;
  color: #14B8A6;
  filter: drop-shadow(0 3px 6px rgba(0, 0, 0, 0.5));
}

@keyframes bounce-vertical {
  0%, 100% {
    transform: translateX(-50%) translateY(0);
  }
  50% {
    transform: translateX(-50%) translateY(10px);
  }
}

@keyframes pulse {
  0%, 100% {
    box-shadow: 0 0 0 0 rgba(255, 255, 255, 0.4);
  }
  50% {
    box-shadow: 0 0 0 10px rgba(255, 255, 255, 0);
  }
}

/* Animations */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateX(50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.animate-fade-in {
  animation: fadeIn 0.8s ease-out;
}

.animate-fade-in-delay {
  animation: fadeIn 0.8s ease-out 0.2s backwards;
}

.animate-fade-in-delay-2 {
  animation: fadeIn 0.8s ease-out 0.4s backwards;
}

.animate-fade-in-delay-3 {
  animation: fadeIn 0.8s ease-out 0.6s backwards;
}

.animate-fade-in-delay-4 {
  animation: fadeIn 0.8s ease-out 0.8s backwards;
}

.animate-slide-in {
  animation: slideIn 1s ease-out 0.3s backwards;
}

/* Responsive Design */
@media (max-width: 968px) {
  .hero-content {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .hero-image {
    order: -1;
  }

  .hero-title {
    font-size: 2.5rem;
  }

  .hero-subtitle {
    font-size: 1.5rem;
  }

  .hero-stats {
    justify-content: center;
  }

  .hero-buttons {
    justify-content: center;
  }

  .hero-social {
    justify-content: center;
  }

  /* Simplify badges on tablet */
  .image-container {
    width: 350px;
    height: 350px;
  }

  .image-placeholder {
    width: 280px;
    height: 280px;
    font-size: 100px;
  }

  .floating-badge {
    font-size: 0.75rem;
    padding: 8px 14px;
  }

  .badge-main {
    padding: 10px 18px;
    font-size: 0.85rem;
  }
  
  /* Hide some badges on medium screens */
  .badge-7, .badge-8, .badge-9 {
    display: none;
  }
}

@media (max-width: 640px) {
  .hero-title {
    font-size: 2rem;
  }

  .hero-subtitle {
    font-size: 1.3rem;
  }

  .hero-description {
    font-size: 1rem;
  }

  .hero-stats {
    gap: 15px;
    flex-wrap: wrap;
  }

  .stat-item {
    padding: 10px 15px;
    flex: 1;
    min-width: 100px;
  }

  .stat-item strong {
    font-size: 1.5rem;
  }

  .image-container {
    width: 280px;
    height: 280px;
  }

  .image-placeholder {
    width: 220px;
    height: 220px;
    font-size: 80px;
  }

  .hero-buttons {
    flex-direction: column;
    width: 100%;
  }

  .btn {
    width: 100%;
    text-align: center;
    justify-content: center;
  }

  /* Only show main badges on mobile */
  .floating-badge {
    display: none;
  }

  .badge-main.badge-1,
  .badge-main.badge-2 {
    display: flex;
    font-size: 0.7rem;
    padding: 8px 12px;
  }

  .badge-main.badge-1 {
    top: 0%;
    right: -5%;
  }

  .badge-main.badge-2 {
    bottom: 0%;
    left: -5%;
  }
}
</style>
