<template>
  <section id="contact" class="contact">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Start Your Digital Transformation</h2>
        <p class="section-subtitle">Ready to scale your business with enterprise-grade IT solutions? Let's discuss your strategic technology needs and ROI objectives.</p>
      </div>
      
      <div class="contact-content">
        <div class="contact-info">
          <h3>Transform Your Business Today</h3>
          <p>I partner with forward-thinking companies to deliver enterprise-grade technology solutions that drive measurable business growth. From digital transformation to cloud infrastructure, I provide strategic IT consulting that delivers real ROI.</p>
          
          <div class="contact-methods">
            <div class="contact-method">
              <div class="method-icon">
                <i class="fas fa-envelope"></i>
              </div>
              <div class="method-content">
                <h4>Business Email</h4>
                <a href="mailto:business@yourcompany.com">business@yourcompany.com</a>
              </div>
            </div>
            
            <div class="contact-method">
              <div class="method-icon">
                <i class="fas fa-phone"></i>
              </div>
              <div class="method-content">
                <h4>Direct Line</h4>
                <a href="tel:+62812345678">+62 812-345-678</a>
              </div>
            </div>
            
            <div class="contact-method">
              <div class="method-icon">
                <i class="fas fa-map-marker-alt"></i>
              </div>
              <div class="method-content">
                <h4>Location</h4>
                <span>Jakarta, Indonesia</span>
              </div>
            </div>
            
            <div class="contact-method">
              <div class="method-icon">
                <i class="fas fa-clock"></i>
              </div>
              <div class="method-content">
                <h4>Response Time</h4>
                <span>Within 4 business hours</span>
              </div>
            </div>
          </div>
          
          <div class="availability">
            <h4>Current Availability</h4>
            <div class="availability-status">
              <div class="status-indicator available"></div>
              <span>Accepting enterprise projects (Q1 2025)</span>
            </div>
            <p class="availability-note">Currently booking strategic consulting and development projects for Q1 2025. Priority given to enterprise clients with $25K+ budgets.</p>
          </div>
          
          <div class="social-links">
            <h4>Professional Network</h4>
            <div class="social-grid">
              <a v-for="social in socialLinks" :key="social.name" :href="social.url" target="_blank" class="social-link">
                <i :class="social.icon"></i>
                <span>{{ social.name }}</span>
              </a>
            </div>
          </div>
        </div>
        
        <div class="contact-form">
          <form @submit.prevent="submitForm" ref="contactFormRef">
            <div class="form-row">
              <div class="form-group">
                <label for="firstName">First Name *</label>
                <input 
                  type="text" 
                  id="firstName" 
                  v-model="form.firstName" 
                  required
                  :class="{ error: errors.firstName }"
                >
                <span v-if="errors.firstName" class="error-message">{{ errors.firstName }}</span>
              </div>
              <div class="form-group">
                <label for="lastName">Last Name *</label>
                <input 
                  type="text" 
                  id="lastName" 
                  v-model="form.lastName" 
                  required
                  :class="{ error: errors.lastName }"
                >
                <span v-if="errors.lastName" class="error-message">{{ errors.lastName }}</span>
              </div>
            </div>
            
            <div class="form-group">
              <label for="email">Email Address *</label>
              <input 
                type="email" 
                id="email" 
                v-model="form.email" 
                required
                :class="{ error: errors.email }"
              >
              <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
            </div>
            
            <div class="form-group">
              <label for="phone">Phone Number</label>
              <input 
                type="tel" 
                id="phone" 
                v-model="form.phone"
                :class="{ error: errors.phone }"
              >
              <span v-if="errors.phone" class="error-message">{{ errors.phone }}</span>
            </div>
            
            <div class="form-group">
              <label for="company">Company/Organization</label>
              <input 
                type="text" 
                id="company" 
                v-model="form.company"
              >
            </div>
            
            <div class="form-group">
              <label for="service">Service Needed</label>
              <select id="service" v-model="form.service">
                <option value="">Select a service...</option>
                <option value="enterprise-web-development">Enterprise Web Development ($15K+)</option>
                <option value="cloud-infrastructure">Cloud Infrastructure & DevOps ($25K+)</option>
                <option value="digital-transformation">Digital Transformation Consulting ($300/hr)</option>
                <option value="api-development">API Integration & Development ($8K+)</option>
                <option value="database-optimization">Database Design & Optimization ($5K+)</option>
                <option value="enterprise-support">Enterprise Support & Maintenance ($2.5K/mo)</option>
                <option value="other">Custom Enterprise Solution</option>
              </select>
            </div>
            
            <div class="form-group">
              <label for="budget">Investment Budget</label>
              <select id="budget" v-model="form.budget">
                <option value="">Select investment range...</option>
                <option value="under-25k">Under $25,000</option>
                <option value="25k-50k">$25,000 - $50,000</option>
                <option value="50k-100k">$50,000 - $100,000</option>
                <option value="100k-250k">$100,000 - $250,000</option>
                <option value="over-250k">Over $250,000</option>
              </select>
            </div>
            
            <div class="form-group">
              <label for="timeline">Implementation Timeline</label>
              <select id="timeline" v-model="form.timeline">
                <option value="">Select timeline...</option>
                <option value="asap">Immediate Start (Rush Project)</option>
                <option value="1-month">Within 1 month</option>
                <option value="2-3-months">2-3 months</option>
                <option value="3-6-months">3-6 months (Preferred)</option>
                <option value="6-12-months">6-12 months (Strategic Planning)</option>
                <option value="flexible">Flexible Timeline</option>
              </select>
            </div>
            
            <div class="form-group">
              <label for="message">Business Requirements & Objectives *</label>
              <textarea 
                id="message" 
                v-model="form.message" 
                rows="5" 
                placeholder="Describe your business challenges, technology requirements, expected ROI, and strategic objectives. Include any current systems that need integration or replacement..."
                required
                :class="{ error: errors.message }"
              ></textarea>
              <span v-if="errors.message" class="error-message">{{ errors.message }}</span>
            </div>
            
            <div class="form-group checkbox-group">
              <label class="checkbox-label">
                <input type="checkbox" v-model="form.newsletter">
                <span class="checkmark"></span>
                Subscribe to exclusive enterprise technology insights and industry reports
              </label>
            </div>
            
            <button type="submit" class="submit-btn" :disabled="isSubmitting">
              <span v-if="!isSubmitting">
                <i class="fas fa-rocket"></i>
                Request Strategic Consultation
              </span>
              <span v-else>
                <i class="fas fa-spinner fa-spin"></i>
                Processing Request...
              </span>
            </button>
          </form>
          
          <div v-if="submitStatus" class="submit-message" :class="submitStatus">
            <i :class="submitStatus === 'success' ? 'fas fa-check-circle' : 'fas fa-exclamation-circle'"></i>
            {{ submitMessage }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue'

const contactFormRef = ref(null)
const isSubmitting = ref(false)
const submitStatus = ref('')
const submitMessage = ref('')

const form = reactive({
  firstName: '',
  lastName: '',
  email: '',
  phone: '',
  company: '',
  service: '',
  budget: '',
  timeline: '',
  message: '',
  newsletter: false
})

const errors = reactive({
  firstName: '',
  lastName: '',
  email: '',
  phone: '',
  message: ''
})

const socialLinks = [
  { name: 'LinkedIn', url: 'https://linkedin.com/in/yourprofile', icon: 'fab fa-linkedin' },
  { name: 'GitHub', url: 'https://github.com/yourusername', icon: 'fab fa-github' },
  { name: 'Medium', url: 'https://medium.com/@yourusername', icon: 'fab fa-medium' },
  { name: 'Telegram', url: 'https://t.me/yourusername', icon: 'fab fa-telegram' }
]

const validateForm = () => {
  // Reset errors
  Object.keys(errors).forEach(key => errors[key] = '')
  
  let isValid = true
  
  if (!form.firstName.trim()) {
    errors.firstName = 'First name is required'
    isValid = false
  }
  
  if (!form.lastName.trim()) {
    errors.lastName = 'Last name is required'
    isValid = false
  }
  
  if (!form.email.trim()) {
    errors.email = 'Email is required'
    isValid = false
  } else if (!/\S+@\S+\.\S+/.test(form.email)) {
    errors.email = 'Please enter a valid email address'
    isValid = false
  }
  
  if (form.phone && !/^[\+]?[1-9][\d]{0,15}$/.test(form.phone.replace(/\s/g, ''))) {
    errors.phone = 'Please enter a valid phone number'
    isValid = false
  }
  
  if (!form.message.trim()) {
    errors.message = 'Business requirements description is required'
    isValid = false
  } else if (form.message.trim().length < 20) {
    errors.message = 'Please provide detailed business requirements (minimum 20 characters)'
    isValid = false
  }
  
  return isValid
}

const submitForm = async () => {
  if (!validateForm()) {
    return
  }
  
  isSubmitting.value = true
  submitStatus.value = ''
  
  try {
    // Simulate form submission (replace with actual API call)
    await new Promise(resolve => setTimeout(resolve, 2000))
    
    // Here you would typically send the form data to your backend
    console.log('Form submitted:', form)
    
    submitStatus.value = 'success'
    submitMessage.value = 'Thank you for your interest! I\'ll review your requirements and respond within 4 business hours with a strategic consultation proposal.'
    
    // Reset form
    Object.keys(form).forEach(key => {
      if (typeof form[key] === 'boolean') {
        form[key] = false
      } else {
        form[key] = ''
      }
    })
    
    // Reset form validation state
    contactFormRef.value.reset()
    
  } catch (error) {
    console.error('Form submission error:', error)
    submitStatus.value = 'error'
    submitMessage.value = 'Sorry, there was an error processing your request. Please contact me directly at business@yourcompany.com or try again.'
  } finally {
    isSubmitting.value = false
    
    // Clear message after 5 seconds
    setTimeout(() => {
      submitStatus.value = ''
      submitMessage.value = ''
    }, 5000)
  }
}
</script>

<style scoped>
.contact {
  padding: 100px 0;
  background: linear-gradient(135deg, #1B3C53 0%, #456882 100%);
  color: white;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 5%;
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.section-subtitle {
  font-size: 1.1rem;
  max-width: 600px;
  margin: 0 auto;
  opacity: 0.9;
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 4rem;
  align-items: start;
}

.contact-info h3 {
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
}

.contact-info > p {
  font-size: 1.1rem;
  line-height: 1.7;
  margin-bottom: 2.5rem;
  opacity: 0.9;
}

.contact-methods {
  margin-bottom: 3rem;
}

.contact-method {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.method-icon {
  width: 50px;
  height: 50px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  backdrop-filter: blur(10px);
}

.method-content h4 {
  margin-bottom: 0.3rem;
  font-size: 1rem;
}

.method-content a {
  color: #D2C1B6;
  text-decoration: none;
}

.method-content a:hover {
  text-decoration: underline;
}

.method-content span {
  opacity: 0.8;
}

.availability {
  margin-bottom: 3rem;
}

.availability h4 {
  margin-bottom: 1rem;
}

.availability-status {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  margin-bottom: 0.8rem;
}

.status-indicator {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.status-indicator.available {
  background: #D2C1B6;
  box-shadow: 0 0 10px rgba(210, 193, 182, 0.5);
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% { box-shadow: 0 0 0 0 rgba(210, 193, 182, 0.7); }
  70% { box-shadow: 0 0 0 10px rgba(210, 193, 182, 0); }
  100% { box-shadow: 0 0 0 0 rgba(210, 193, 182, 0); }
}

.availability-note {
  font-size: 0.9rem;
  opacity: 0.8;
}

.social-links h4 {
  margin-bottom: 1rem;
}

.social-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
}

.social-link {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  padding: 0.8rem;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 10px;
  color: white;
  text-decoration: none;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.social-link:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-2px);
}

.contact-form {
  background: rgba(255, 255, 255, 0.1);
  padding: 2.5rem;
  border-radius: 20px;
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
}

.form-group input,
.form-group select,
.form-group textarea {
  width: 100%;
  padding: 12px 16px;
  border: 2px solid rgba(255, 255, 255, 0.2);
  border-radius: 10px;
  background: rgba(255, 255, 255, 0.1);
  color: white;
  font-size: 1rem;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: rgba(255, 255, 255, 0.6);
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #D2C1B6;
  background: rgba(255, 255, 255, 0.15);
}

.form-group input.error,
.form-group textarea.error {
  border-color: #e74c3c;
}

.error-message {
  color: #e74c3c;
  font-size: 0.9rem;
  margin-top: 0.3rem;
  display: block;
}

.checkbox-group {
  display: flex;
  align-items: flex-start;
  gap: 0.8rem;
}

.checkbox-label {
  display: flex;
  align-items: flex-start;
  gap: 0.8rem;
  cursor: pointer;
  font-size: 0.9rem;
  line-height: 1.4;
  margin-bottom: 0 !important;
}

.checkbox-label input[type="checkbox"] {
  display: none;
}

.checkmark {
  width: 20px;
  height: 20px;
  border: 2px solid rgba(255, 255, 255, 0.4);
  border-radius: 4px;
  position: relative;
  background: transparent;
  transition: all 0.3s ease;
  flex-shrink: 0;
  margin-top: 2px;
}

.checkbox-label input[type="checkbox"]:checked + .checkmark {
  background: #D2C1B6;
  border-color: #D2C1B6;
}

.checkbox-label input[type="checkbox"]:checked + .checkmark::after {
  content: '';
  position: absolute;
  left: 6px;
  top: 2px;
  width: 6px;
  height: 10px;
  border: solid #1B3C53;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
}

.submit-btn {
  width: 100%;
  padding: 15px;
  background: #D2C1B6;
  color: #1B3C53;
  border: none;
  border-radius: 10px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.8rem;
}

.submit-btn:hover:not(:disabled) {
  background: rgba(210, 193, 182, 0.8);
  transform: translateY(-2px);
}

.submit-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.submit-message {
  margin-top: 1.5rem;
  padding: 1rem;
  border-radius: 10px;
  display: flex;
  align-items: center;
  gap: 0.8rem;
  font-weight: 500;
}

.submit-message.success {
  background: rgba(210, 193, 182, 0.2);
  border: 1px solid rgba(210, 193, 182, 0.4);
  color: #D2C1B6;
}

.submit-message.error {
  background: rgba(231, 76, 60, 0.2);
  border: 1px solid rgba(231, 76, 60, 0.4);
  color: #e74c3c;
}

@media (max-width: 768px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .form-row {
    grid-template-columns: 1fr;
  }
  
  .social-grid {
    grid-template-columns: 1fr;
  }
  
  .contact-form {
    padding: 1.5rem;
  }
  
  .section-title {
    font-size: 2rem;
  }
}
</style>
