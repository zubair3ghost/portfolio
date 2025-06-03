

<template>
  <div class="contact-form-container">
    <div class="form-wrapper">
      <h2 class="form-title">Contact Us</h2>
      <form @submit.prevent="submitForm" class="contact-form">
        <div class="form-group">
          <label for="name" class="form-label">Name *</label>
          <input
            type="text"
            id="name"
            v-model="form.name"
            class="form-input"
            placeholder="Enter your full name"
            required
          />
        </div>

        <div class="form-group">
          <label for="email" class="form-label">Email *</label>
          <input
            type="email"
            id="email"
            v-model="form.email"
            class="form-input"
            placeholder="Enter your email address"
            required
          />
        </div>

        <div class="form-group">
          <label for="phone" class="form-label">Phone Number</label>
          <input
            type="tel"
            id="phone"
            v-model="form.phone"
            class="form-input"
            placeholder="Enter your phone number"
          />
        </div>

        <div class="form-group">
          <label for="message" class="form-label">Message *</label>
          <textarea
            id="message"
            v-model="form.message"
            class="form-textarea"
            rows="5"
            placeholder="Enter your message"
            required
          ></textarea>
        </div>

        <button type="submit" class="submit-btn" :disabled="isSubmitting">
          <span v-if="!isSubmitting">Send Message</span>
          <span v-else>Sending...</span>
        </button>
      </form>

      <!-- Success/Error Messages -->
      <div v-if="successMessage" class="success-message">
        {{ successMessage }}
      </div>
      <div v-if="errorMessage" class="error-message">
        {{ errorMessage }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContactForm',
  data() {
    return {
      form: {
        name: '',
        email: '',
        phone: '',
        message: ''
      },
      isSubmitting: false,
      successMessage: '',
      errorMessage: ''
    }
  },
  methods: {
    async submitForm() {
      this.isSubmitting = true;
      this.successMessage = '';
      this.errorMessage = '';

      try {
        // Simulate form submission - replace with your actual API call
        await new Promise(resolve => setTimeout(resolve, 1000));
        
        // Handle successful submission
        this.successMessage = 'Message sent successfully! We\'ll get back to you soon.';
        this.resetForm();
      } catch (error) {
        this.errorMessage = 'Failed to send message. Please try again later.';
      } finally {
        this.isSubmitting = false;
      }
    },
    resetForm() {
      this.form = {
        name: '',
        email: '',
        phone: '',
        message: ''
      };
    }
  }
}
</script>

<style scoped>
.contact-form-container {
  min-height: 100vh;
  background: #18181b;
  padding: 2rem 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.form-wrapper {
  background: rgba(40, 40, 40, 0.95);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
  padding: 2.5rem;
  width: 100%;
  max-width: 600px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.form-title {
  color: #ffffff;
  font-size: 2rem;
  font-weight: 600;
  text-align: center;
  margin-bottom: 2rem;
  background: linear-gradient(135deg, #ffffff, #a0a0a0);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-label {
  color: #e0e0e0;
  font-size: 0.95rem;
  font-weight: 500;
  margin-bottom: 0.5rem;
  letter-spacing: 0.3px;
}

.form-input,
.form-textarea {
  background: rgba(255, 255, 255, 0.05);
  border: 2px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  padding: 0.875rem 1rem;
  color: #ffffff;
  font-size: 1rem;
  transition: all 0.3s ease;
  outline: none;
}

.form-input::placeholder,
.form-textarea::placeholder {
  color: rgba(255, 255, 255, 0.4);
}

.form-input:focus,
.form-textarea:focus {
  border-color: #60a5fa;
  box-shadow: 0 0 0 3px rgba(96, 165, 250, 0.1);
  background: rgba(255, 255, 255, 0.08);
}

.form-textarea {
  resize: vertical;
  min-height: 120px;
  font-family: inherit;
}

.submit-btn {
  background: linear-gradient(135deg, #60a5fa, #3b82f6);
  color: #ffffff;
  border: none;
  border-radius: 8px;
  padding: 1rem 2rem;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-top: 1rem;
  position: relative;
  overflow: hidden;
}

.submit-btn:hover:not(:disabled) {
  background: linear-gradient(135deg, #3b82f6, #2563eb);
  transform: translateY(-2px);
  box-shadow: 0 10px 25px rgba(96, 165, 250, 0.4);
}

.submit-btn:active:not(:disabled) {
  transform: translateY(0);
}

.submit-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
  transform: none;
}

.success-message {
  background: rgba(34, 197, 94, 0.1);
  border: 1px solid rgba(34, 197, 94, 0.3);
  color: #4ade80;
  padding: 1rem;
  border-radius: 8px;
  margin-top: 1rem;
  text-align: center;
  font-weight: 500;
}

.error-message {
  background: rgba(239, 68, 68, 0.1);
  border: 1px solid rgba(239, 68, 68, 0.3);
  color: #f87171;
  padding: 1rem;
  border-radius: 8px;
  margin-top: 1rem;
  text-align: center;
  font-weight: 500;
}

/* Responsive Design */
@media (max-width: 768px) {
  .contact-form-container {
    padding: 1rem;
  }

  .form-wrapper {
    padding: 2rem 1.5rem;
  }

  .form-title {
    font-size: 1.75rem;
    margin-bottom: 1.5rem;
  }

  .contact-form {
    gap: 1.25rem;
  }

  .form-input,
  .form-textarea {
    padding: 0.75rem;
    font-size: 0.95rem;
  }

  .submit-btn {
    padding: 0.875rem 1.5rem;
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .form-wrapper {
    padding: 1.5rem 1rem;
  }

  .form-title {
    font-size: 1.5rem;
  }

  .form-input,
  .form-textarea {
    padding: 0.625rem 0.75rem;
  }

  .submit-btn {
    padding: 0.75rem 1.25rem;
    font-size: 0.95rem;
  }
}

/* Loading animation */
@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.submit-btn:disabled span {
  animation: pulse 1.5s infinite;
}
</style>




















<!-- <template>
  <section id="contact" class="contact-section">
    <h2 class="section-title">Contact Me</h2>
    <transition name="fade-slide-up" appear>
      <div class="contact-card">
        <transition name="fade" mode="out-in">
          <form
            v-if="!submitted"
            key="form"
            class="contact-form"
            @submit.prevent="onSubmit"
            autocomplete="off"
          >
            <div class="input-group">
              <label for="name">Name</label>
              <input
                id="name"
                v-model="form.name"
                type="text"
                placeholder="Your name"
                :class="{ invalid: errors.name }"
                @input="clearError('name')"
                required
              />
              <transition name="fade">
                <span v-if="errors.name" class="error">{{ errors.name }}</span>
              </transition>
            </div>
            <div class="input-group">
              <label for="email">Email</label>
              <input
                id="email"
                v-model="form.email"
                type="email"
                placeholder="you@email.com"
                :class="{ invalid: errors.email }"
                @input="clearError('email')"
                required
              />
              <transition name="fade">
                <span v-if="errors.email" class="error">{{ errors.email }}</span>
              </transition>
            </div>
            <div class="input-group">
              <label for="message">Message</label>
              <textarea
                id="message"
                v-model="form.message"
                rows="4"
                placeholder="Type your message..."
                :class="{ invalid: errors.message }"
                @input="clearError('message')"
                required
              ></textarea>
              <transition name="fade">
                <span v-if="errors.message" class="error">{{ errors.message }}</span>
              </transition>
            </div>
            <transition name="btn-pop">
              <button
                class="btn"
                type="submit"
                :disabled="loading"
                v-if="!loading"
              >
                <i class="fas fa-paper-plane"></i> Send Message
              </button>
            </transition>
            <transition name="fade">
              <div class="sending" v-if="loading">
                <i class="fas fa-spinner fa-spin"></i> Sending...
              </div>
            </transition>
          </form>
          <div v-else key="success" class="success-message">
            <transition name="fade">
              <div>
                <i class="fas fa-check-circle"></i>
                <p>Thank you for reaching out!<br />I'll get back to you soon.</p>
                <button class="btn secondary" @click="resetForm">
                  Send Another Message
                </button>
              </div>
            </transition>
          </div>
        </transition>
        <transition name="fade">
          <div class="contact-links">
            <a
              href="mailto:youremail@example.com"
              target="_blank"
              title="Email"
              class="icon-link"
            >
              <i class="fas fa-envelope"></i>
            </a>
            <a
              href="https://github.com/yourgithub"
              target="_blank"
              title="GitHub"
              class="icon-link"
            >
              <i class="fab fa-github"></i>
            </a>
            <a
              href="https://linkedin.com/in/yourlinkedin"
              target="_blank"
              title="LinkedIn"
              class="icon-link"
            >
              <i class="fab fa-linkedin"></i>
            </a>
          </div>
        </transition>
      </div>
    </transition>
  </section>
</template>

<script>
export default {
  name: "ContactSection",
  data() {
    return {
      form: {
        name: "",
        email: "",
        message: "",
      },
      errors: {},
      loading: false,
      submitted: false,
    };
  },
  methods: {
    clearError(field) {
      this.$set(this.errors, field, "");
    },
    validate() {
      let isValid = true;
      this.errors = {};
      if (!this.form.name.trim()) {
        this.errors.name = "Name is required.";
        isValid = false;
      }
      if (!this.form.email.trim()) {
        this.errors.email = "Email is required.";
        isValid = false;
      } else if (
        !/^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(this.form.email)
      ) {
        this.errors.email = "Please enter a valid email address.";
        isValid = false;
      }
      if (!this.form.message.trim()) {
        this.errors.message = "Message cannot be empty.";
        isValid = false;
      }
      return isValid;
    },
    onSubmit() {
      if (!this.validate()) return;
      this.loading = true;
      setTimeout(() => {
        this.loading = false;
        this.submitted = true;
      }, 1600);
    },
    resetForm() {
      this.form = { name: "", email: "", message: "" };
      this.submitted = false;
      this.errors = {};
    },
  },
};
</script>

<style scoped>
.contact-section {
  background: #23232a;
  padding: 4.5rem 0 3.5rem 0;
  min-height: 70vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.section-title {
  text-align: center;
  color: #7dd3fc;
  font-size: 2.1rem;
  margin-bottom: 2.4rem;
  letter-spacing: 1px;
}
.contact-card {
  background: #18181b;
  box-shadow: 0 4px 28px #0006;
  border-radius: 22px;
  max-width: 440px;
  width: 98vw;
  margin: 0 auto;
  padding: 2.2rem 1.6rem 1.5rem 1.6rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.7rem;
  position: relative;
  transition: box-shadow 0.18s, transform 0.18s;
  animation: popIn 1s;
}
@keyframes popIn {
  from { opacity: 0; transform: translateY(60px) scale(0.9);}
  to { opacity: 1; transform: none;}
} 

.contact-form {
  width: 100%;
  max-width: 400px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 1.12rem;
}
.input-group {
  display: flex;
  flex-direction: column;
  position: relative;   
  /* try to chagne the postion in form  */
  width: 100%;
}
label {
  color: #7dd3fc;
  font-size: 0.97rem;
  margin-bottom: 0.28rem;
  font-weight: 600;
}
input,
textarea {
  background: #23232a;
  color: #e6e6ea;
  border: 2px solid #293042;
  border-radius: 8px;
  font-size: 1.05rem;
  padding: 0.61rem 0.9rem;
  outline: none;
  transition: border 0.19s, box-shadow 0.19s;
  margin-bottom: 0.16rem;
  resize: none;
  box-shadow: 0 2px 8px #0001;
}
input:focus,
textarea:focus {
  border-color: #7dd3fc;
  box-shadow: 0 2px 12px #7dd3fc33;
}
input.invalid,
textarea.invalid {
  border-color: #f87171;
}
.error {
  color: #f87171;
  font-size: 0.93rem;
  margin-top: -0.1rem;
  margin-bottom: 0.12rem;
  transition: opacity 0.2s;
}
.btn {
  background: linear-gradient(90deg, #0ea5e9 0%, #7dd3fc 100%);
  color: #fff;
  border: none;
  border-radius: 8px;
  font-weight: 600;
  padding: 0.7rem 1.7rem;
  font-size: 1rem;
  text-decoration: none;
  box-shadow: 0 4px 16px 0 #2563eb33;
  transition: background 0.22s, transform 0.18s, box-shadow 0.22s;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 0.5rem;
  cursor: pointer;
}
.btn[disabled] {
  filter: grayscale(60%);
  opacity: 0.7;
  cursor: not-allowed;
}
.btn.secondary {
  background: transparent;
  border: 2px solid #7dd3fc;
  color: #7dd3fc;
}
.btn.secondary:hover {
  background: #23232a;
  color: #fff;
}
.btn:hover:not([disabled]) {
  background: linear-gradient(90deg, #7dd3fc 0%, #0ea5e9 100%);
  transform: translateY(-2px) scale(1.04);
  box-shadow: 0 6px 22px 0 #0ea5e988;
}
.sending {
  color: #7dd3fc;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 0.7rem;
  margin-top: 0.7rem;
  font-size: 1.04rem;
}
.success-message {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #7dd3fc;
  font-size: 1.14rem;
  gap: 1.2rem;
  animation: fadeIn 0.7s;
  text-align: center;
}
.success-message i {
  font-size: 2.9rem;
  color: #22c55e;
  filter: drop-shadow(0 0 8px #22c55e66);
}
.success-message p {
  margin-bottom: 0.7rem;
  color: #fff;
}
.fade-enter-active, .fade-leave-active { transition: opacity 0.45s; }
.fade-enter, .fade-leave-to { opacity: 0; }
.fade-slide-up-enter-active, .fade-slide-up-appear-active {
  animation: fadeSlideUp 1.1s;
}
@keyframes fadeSlideUp {
  from { opacity: 0; transform: translateY(60px);}
  to { opacity: 1; transform: none;}
}
.btn-pop-enter-active,
.btn-pop-appear-active {
  animation: btnPop 0.7s cubic-bezier(0.25, 1, 0.5, 1);
}
@keyframes btnPop {
  0% {
    opacity: 0;
    transform: scale(0.7) translateY(20px);
  }
  60% {
    opacity: 1;
    transform: scale(1.09) translateY(-7px);
  }
  100% {
    opacity: 1;
    transform: scale(1) translateY(0);
  }
}
.contact-links {
  display: flex;
  flex-direction: row;
  gap: 1.5rem;
  margin-top: 1.1rem;
  justify-content: center;
  align-items: center;
  width: 100%;
}
.icon-link {
  background: #23232a;
  border-radius: 50%;
  color: #7dd3fc;
  width: 46px;
  height: 46px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.36rem;
  box-shadow: 0 2px 14px #7dd3fc33;
  transition: background 0.18s, color 0.18s, transform 0.18s;
}
.icon-link:hover {
  background: #7dd3fc;
  color: #18181b;
  transform: scale(1.13) rotate(-6deg);
}

/* Tablet and below: more compact padding */
@media (max-width: 700px) {
  .contact-card {
    padding: 1.4rem 1rem 1.1rem 1rem;
    width: 100%;
    /* max-width: 99vw; */
  }
  .contact-form {
    max-width: 100%;
    padding: 0;
  }
}

/* Mobile: smaller padding and icons */
@media (max-width: 500px) {
  .contact-card {
    padding: 1rem;
    border-radius: 13px;
    width: 100%;
    /* max-width: 100vw; */
  }
  .contact-form {
    max-width: 100%;
    padding: 1;
    gap: 0.75rem;
  }
  .contact-links {
    gap: 0.7rem;
  }
  .icon-link {
    width: 35px;
    height: 35px;
    font-size: 1.05rem;
  }
  .success-message {
    font-size: 1rem;
    gap: 0.8rem;
  }
}
</style> -->