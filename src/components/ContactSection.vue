<template>
    <section id="contact" class="contact">
        <div class="container">
            <h2 class="section-title">Get In Touch</h2>
            <p class="section-subtitle">Ready to bring your ideas to life? Let's discuss your next project</p>
            
            <div class="contact-content">
                <div class="contact-info">
                    <div class="info-header">
                        <div class="header-icon">
                            <i class="fas fa-comments"></i>
                        </div>
                        <div>
                            <h3>Let's Work Together</h3>
                            <p class="subtitle">Building innovative solutions for modern businesses</p>
                        </div>
                    </div>
                    
                    <p class="intro-text">
                        I'm currently available for freelance work and full-time opportunities.
                        If you have a project in mind or just want to chat about technology,
                        feel free to reach out!
                    </p>
                    
                    <div class="contact-details">
                        <div class="contact-item">
                            <div class="item-icon">
                                <i class="fas fa-envelope"></i>
                            </div>
                            <div class="item-content">
                                <h4>Email</h4>
                                <a href="mailto:cristparlindungan@gmail.com">cristparlindungan@gmail.com</a>
                            </div>
                        </div>
                        <div class="contact-item">
                            <div class="item-icon">
                                <i class="fas fa-map-marker-alt"></i>
                            </div>
                            <div class="item-content">
                                <h4>Location</h4>
                                <p>Depok, Indonesia</p>
                            </div>
                        </div>
                        <div class="contact-item">
                            <div class="item-icon">
                                <i class="fas fa-clock"></i>
                            </div>
                            <div class="item-content">
                                <h4>Response Time</h4>
                                <p>Usually within 24 hours</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="social-section">
                        <h4>Connect With Me</h4>
                        <div class="social-links">
                            <a href="https://www.linkedin.com/in/cris-parlindungan-96650a1bb/" target="_blank"
                                class="social-link" title="LinkedIn">
                                <i class="fab fa-linkedin-in"></i>
                            </a>
                            
                        </div>
                    </div>
                </div>
                
                <form class="contact-form" @submit.prevent="handleSubmit">
                    <div class="form-header">
                        <i class="fas fa-paper-plane"></i>
                        <h3>Send a Message</h3>
                    </div>
                    
                    <div class="form-grid">
                        <div class="form-group">
                            <label for="name">
                                <i class="fas fa-user"></i>
                                Name
                            </label>
                            <input type="text" id="name" v-model="formData.name" required placeholder="Your name" />
                        </div>
                        <div class="form-group">
                            <label for="email">
                                <i class="fas fa-envelope"></i>
                                Email
                            </label>
                            <input type="email" id="email" v-model="formData.email" required
                                placeholder="your.email@example.com" />
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="subject">
                            <i class="fas fa-tag"></i>
                            Subject
                        </label>
                        <input type="text" id="subject" v-model="formData.subject" required
                            placeholder="Project inquiry" />
                    </div>
                    
                    <div class="form-group">
                        <label for="message">
                            <i class="fas fa-comment-dots"></i>
                            Message
                        </label>
                        <textarea id="message" v-model="formData.message" required rows="5"
                            placeholder="Tell me about your project..."></textarea>
                    </div>
                    
                    <button type="submit" class="btn btn-primary" :disabled="isSubmitting">
                        <i class="fas fa-paper-plane"></i>
                        <span v-if="!isSubmitting">Send Message</span>
                        <span v-else>
                            <i class="fas fa-spinner fa-spin"></i>
                            Sending...
                        </span>
                    </button>
                    
                    <transition name="fade">
                        <div v-if="submitMessage" class="submit-message" :class="submitStatus">
                            <i class="fas fa-check-circle"></i>
                            {{ submitMessage }}
                        </div>
                    </transition>
                </form>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
    name: '',
    email: '',
    subject: '',
    message: ''
})

const isSubmitting = ref(false)
const submitMessage = ref('')
const submitStatus = ref('')

const handleSubmit = () => {
    isSubmitting.value = true
    submitMessage.value = ''

    // Simulate form submission
    setTimeout(() => {
        isSubmitting.value = false
        submitMessage.value = 'Thank you for your message! I will get back to you soon.'
        submitStatus.value = 'success'

        // Reset form
        formData.value = {
            name: '',
            email: '',
            subject: '',
            message: ''
        }

        // Clear message after 5 seconds
        setTimeout(() => {
            submitMessage.value = ''
        }, 5000)
    }, 1500)
}
</script>

<style scoped>
.contact {
    padding: 100px 0;
    background: var(--background-color);
    position: relative;
}

.section-subtitle {
    text-align: center;
    color: var(--text-secondary);
    font-size: 1.1em;
    margin-top: -40px;
    margin-bottom: 60px;
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
}

.contact-content {
    display: grid;
    grid-template-columns: 1fr 1.3fr;
    gap: 60px;
    margin-top: 40px;
}

/* Contact Info */
.contact-info {
    display: flex;
    flex-direction: column;
    gap: 30px;
}

.info-header {
    display: flex;
    gap: 20px;
    align-items: flex-start;
    margin-bottom: 10px;
}

.header-icon {
    width: 60px;
    height: 60px;
    background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
    border-radius: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.8em;
    color: white;
    box-shadow: 0 8px 20px rgba(30, 58, 138, 0.3);
    flex-shrink: 0;
}

.info-header h3 {
    font-size: 2rem;
    color: var(--text-color);
    margin-bottom: 5px;
    font-weight: 700;
}

.info-header .subtitle {
    color: var(--text-secondary);
    font-size: 0.95em;
    margin: 0;
}

.intro-text {
    color: var(--text-secondary);
    line-height: 1.8;
    font-size: 1em;
}

.contact-details {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.contact-item {
    display: flex;
    gap: 18px;
    align-items: flex-start;
    padding: 20px;
    background: var(--surface-color);
    border-radius: 12px;
    border: 2px solid var(--border-color);
    transition: all 0.3s ease;
}

.contact-item:hover {
    border-color: var(--primary-color);
    transform: translateX(5px);
    box-shadow: var(--shadow);
}

.item-icon {
    width: 45px;
    height: 45px;
    background: linear-gradient(135deg, rgba(30, 58, 138, 0.1), rgba(20, 184, 166, 0.1));
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.3em;
    color: var(--primary-color);
    flex-shrink: 0;
}

.item-content h4 {
    color: var(--text-color);
    margin-bottom: 5px;
    font-size: 1em;
    font-weight: 600;
}

.item-content a,
.item-content p {
    color: var(--text-secondary);
    text-decoration: none;
    transition: color 0.3s ease;
    font-size: 0.95em;
    margin: 0;
}

.item-content a:hover {
    color: var(--primary-color);
}

.social-section {
    padding-top: 20px;
}

.social-section h4 {
    color: var(--text-color);
    margin-bottom: 15px;
    font-size: 1.1em;
    font-weight: 600;
}

.social-links {
    display: flex;
    gap: 15px;
}

.social-link {
    width: 50px;
    height: 50px;
    border-radius: 12px;
    background: var(--surface-color);
    border: 2px solid var(--border-color);
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--primary-color);
    font-size: 1.3rem;
    transition: all 0.3s ease;
    text-decoration: none;
}

.social-link:hover {
    background: var(--primary-color);
    border-color: var(--primary-color);
    color: white;
    transform: translateY(-5px);
    box-shadow: 0 8px 20px rgba(30, 58, 138, 0.3);
}

/* Contact Form */
.contact-form {
    background: var(--surface-color);
    padding: 40px;
    border-radius: 20px;
    box-shadow: var(--shadow-lg);
    border: 2px solid var(--border-color);
    transition: all 0.3s ease;
}

.form-header {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 35px;
    padding-bottom: 20px;
    border-bottom: 2px solid var(--border-color);
}

.form-header i {
    font-size: 1.8em;
    color: var(--primary-color);
}

.form-header h3 {
    font-size: 1.6em;
    color: var(--text-color);
    margin: 0;
    font-weight: 700;
}

.form-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
}

.form-group {
    margin-bottom: 25px;
}

.form-group label {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 10px;
    color: var(--text-color);
    font-weight: 600;
    font-size: 0.95em;
}

.form-group label i {
    color: var(--primary-color);
    font-size: 0.9em;
}

.form-group input,
.form-group textarea {
    width: 100%;
    padding: 14px 16px;
    border: 2px solid var(--border-color);
    border-radius: 10px;
    font-family: inherit;
    font-size: 1rem;
    transition: all 0.3s ease;
    background: var(--background-color);
    color: var(--text-color);
}

.form-group input:focus,
.form-group textarea:focus {
    outline: none;
    border-color: var(--primary-color);
    box-shadow: 0 0 0 4px rgba(30, 58, 138, 0.1);
}

.form-group textarea {
    resize: vertical;
    min-height: 140px;
}

.btn {
    padding: 16px 36px;
    border-radius: 12px;
    text-decoration: none;
    font-weight: 700;
    transition: all 0.3s ease;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    border: none;
    cursor: pointer;
    font-size: 1.05rem;
    width: 100%;
}

.btn-primary {
    background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
    color: white;
    box-shadow: 0 8px 20px rgba(30, 58, 138, 0.3);
    position: relative;
    overflow: hidden;
}

.btn-primary::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, var(--secondary-color), var(--primary-color));
    transition: left 0.3s ease;
}

.btn-primary:hover:not(:disabled)::before {
    left: 0;
}

.btn-primary:hover:not(:disabled) {
    transform: translateY(-3px);
    box-shadow: 0 12px 30px rgba(30, 58, 138, 0.4);
}

.btn-primary span,
.btn-primary i {
    position: relative;
    z-index: 1;
}

.btn-primary:disabled {
    opacity: 0.7;
    cursor: not-allowed;
}

.submit-message {
    margin-top: 20px;
    padding: 16px 20px;
    border-radius: 12px;
    text-align: center;
    font-weight: 600;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

.submit-message.success {
    background: linear-gradient(135deg, rgba(16, 185, 129, 0.1), rgba(20, 184, 166, 0.1));
    color: var(--secondary-color);
    border: 2px solid var(--secondary-color);
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}

/* Responsive Design */
@media (max-width: 968px) {
    .contact {
        padding: 60px 0;
    }

    .contact-content {
        grid-template-columns: 1fr;
        gap: 40px;
    }

    .form-grid {
        grid-template-columns: 1fr;
    }

    .contact-form {
        padding: 30px 20px;
    }

    .info-header {
        flex-direction: column;
        align-items: center;
        text-align: center;
    }

    .contact-item:hover {
        transform: translateY(-3px);
    }
}

@media (max-width: 640px) {
    .header-icon {
        width: 50px;
        height: 50px;
        font-size: 1.5em;
    }

    .info-header h3 {
        font-size: 1.6rem;
    }

    .item-icon {
        width: 40px;
        height: 40px;
        font-size: 1.1em;
    }

    .social-link {
        width: 45px;
        height: 45px;
        font-size: 1.1rem;
    }
}
</style>
