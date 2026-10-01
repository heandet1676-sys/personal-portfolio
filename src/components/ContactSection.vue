<template>
  <section id="contact" class="section-padding" style="background:var(--bg-secondary)">
    <div class="container">
      <div class="text-center mb-5 reveal">
        <span class="section-label">Get In Touch</span>
        <h2 class="section-title">Let's Build Something <span class="gradient-text">Together</span></h2>
        <div class="section-divider mx-auto"></div>
        <p class="section-subtitle mx-auto">Have a project, idea, or opportunity? I would love to hear about it.</p>
      </div>

      <div class="contact-layout">
        <!-- Info side -->
        <div class="contact-info reveal">
          <div class="contact-info-card glass-card">
            <h3 class="info-heading">Contact Information</h3>
            <p class="info-desc">Feel free to reach out through any channel. I typically respond within 24 hours.</p>

            <div class="contact-items">
              <a :href="'mailto:' + contactInfo.email" class="contact-item">
                <div class="contact-icon">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
                </div>
                <div>
                  <p class="contact-item-label">Email</p>
                  <p class="contact-item-value">{{ contactInfo.email }}</p>
                </div>
              </a>

              <a :href="'tel:' + contactInfo.phone" class="contact-item">
                <div class="contact-icon">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12 19.79 19.79 0 0 1 1.61 3.41C1.61 2.18 2.55 1 3.78 1h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 8.91a16 16 0 0 0 6 6l.91-.91a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
                </div>
                <div>
                  <p class="contact-item-label">Phone</p>
                  <p class="contact-item-value">{{ contactInfo.phone }}</p>
                </div>
              </a>

              <div class="contact-item">
                <div class="contact-icon">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
                </div>
                <div>
                  <p class="contact-item-label">Location</p>
                  <p class="contact-item-value">{{ contactInfo.location }}</p>
                </div>
              </div>
            </div>

            <!-- Social links -->
            <div class="social-links">
              <p class="social-label">Find me on</p>
              <div class="social-row">
                <a v-for="social in socials" :key="social.name" :href="social.url" target="_blank" rel="noopener" class="social-btn" :aria-label="social.name">
                  <span v-html="social.icon"></span>
                  <span>{{ social.name }}</span>
                </a>
              </div>
            </div>
          </div>
        </div>

        <!-- Form side -->
        <div class="contact-form reveal" style="transition-delay:0.15s">
          <div class="form-card glass-card">
            <h3 class="form-heading">Send a Message</h3>
            <form @submit.prevent="submitForm" novalidate>
              <div class="form-row">
                <div class="form-group">
                  <label class="form-label" for="name">Full Name</label>
                  <input id="name" v-model="form.name" type="text" class="form-input" :class="{ error: errors.name }" placeholder="Your name" required autocomplete="name"/>
                  <span class="form-error" v-if="errors.name">{{ errors.name }}</span>
                </div>
                <div class="form-group">
                  <label class="form-label" for="email">Email Address</label>
                  <input id="email" v-model="form.email" type="email" class="form-input" :class="{ error: errors.email }" placeholder="your@email.com" required autocomplete="email"/>
                  <span class="form-error" v-if="errors.email">{{ errors.email }}</span>
                </div>
              </div>
              <div class="form-group">
                <label class="form-label" for="subject">Subject</label>
                <input id="subject" v-model="form.subject" type="text" class="form-input" :class="{ error: errors.subject }" placeholder="What is this about?" required/>
                <span class="form-error" v-if="errors.subject">{{ errors.subject }}</span>
              </div>
              <div class="form-group">
                <label class="form-label" for="message">Message</label>
                <textarea id="message" v-model="form.message" class="form-input form-textarea" :class="{ error: errors.message }" placeholder="Tell me about your project or idea..." rows="5" required></textarea>
                <span class="form-error" v-if="errors.message">{{ errors.message }}</span>
              </div>
              <button type="submit" class="btn-primary-custom w-100 justify-content-center" :disabled="submitting">
                <span v-if="!submitting">
                  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
                  Send Message
                </span>
                <span v-else class="mono" style="font-size:0.85rem">Sending...</span>
              </button>
              <div class="form-success" v-if="submitted">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>
                Message sent successfully! I will get back to you soon.
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ContactSection',
  data() {
    return {
      form: { name: '', email: '', subject: '', message: '' },
      errors: {},
      submitting: false,
      submitted: false,
      contactInfo: {
        email: 'heandet@example.com',
        phone: '+855 XX XXX XXXX',
        location: 'Phnom Penh, Cambodia'
      },
      socials: [
        {
          name: 'GitHub',
          url: 'https://github.com/heandet',
          icon: '<svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>'
        },
        {
          name: 'LinkedIn',
          url: 'https://linkedin.com/in/heandet',
          icon: '<svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>'
        },
        {
          name: 'Facebook',
          url: 'https://facebook.com/heandet',
          icon: '<svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>'
        }
      ]
    }
  },
  methods: {
    validate() {
      const errs = {}
      if (!this.form.name.trim()) errs.name = 'Name is required'
      if (!this.form.email.trim()) errs.email = 'Email is required'
      else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(this.form.email)) errs.email = 'Enter a valid email'
      if (!this.form.subject.trim()) errs.subject = 'Subject is required'
      if (!this.form.message.trim()) errs.message = 'Message is required'
      this.errors = errs
      return Object.keys(errs).length === 0
    },
    async submitForm() {
      if (!this.validate()) return
      this.submitting = true
      // Simulate async send
      await new Promise(r => setTimeout(r, 1400))
      this.submitting = false
      this.submitted = true
      this.form = { name: '', email: '', subject: '', message: '' }
      this.errors = {}
      setTimeout(() => { this.submitted = false }, 6000)
    }
  }
}
</script>

<style scoped>
.contact-layout { display: grid; grid-template-columns: 1fr 1.5fr; gap: 2rem; align-items: start; }
/* Info */
.contact-info-card { padding: 2rem; border-radius: var(--radius-xl); }
.info-heading { font-size: 1.1rem; font-weight: 700; margin-bottom: 0.5rem; }
.info-desc { font-size: 0.85rem; color: var(--text-secondary); line-height: 1.7; margin-bottom: 1.75rem; }
.contact-items { display: flex; flex-direction: column; gap: 1.25rem; margin-bottom: 2rem; }
.contact-item {
  display: flex; align-items: flex-start; gap: 1rem;
  text-decoration: none; color: inherit; transition: var(--transition);
}
.contact-item:hover .contact-icon { background: rgba(99,102,241,0.2); }
.contact-icon {
  width: 42px; height: 42px; flex-shrink: 0;
  background: rgba(99,102,241,0.08); border: 1px solid rgba(99,102,241,0.18);
  border-radius: var(--radius-sm);
  display: flex; align-items: center; justify-content: center;
  color: var(--accent-light); transition: var(--transition);
}
.contact-item-label { font-size: 0.72rem; color: var(--text-muted); margin: 0 0 0.2rem; font-family: var(--font-mono); }
.contact-item-value { font-size: 0.9rem; font-weight: 500; margin: 0; }

/* Social */
.social-label { font-size: 0.78rem; color: var(--text-muted); margin-bottom: 0.75rem; }
.social-row { display: flex; flex-direction: column; gap: 0.5rem; }
.social-btn {
  display: flex; align-items: center; gap: 0.75rem;
  padding: 0.6rem 1rem;
  background: rgba(255,255,255,0.03); border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  text-decoration: none; color: var(--text-secondary);
  font-size: 0.875rem; font-weight: 500; transition: var(--transition);
}
.social-btn:hover { border-color: var(--border-accent); color: var(--accent-light); background: rgba(99,102,241,0.06); }

/* Form */
.form-card { padding: 2rem; border-radius: var(--radius-xl); }
.form-heading { font-size: 1.1rem; font-weight: 700; margin-bottom: 1.5rem; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
.form-group { display: flex; flex-direction: column; gap: 0.4rem; margin-bottom: 1rem; }
.form-label { font-size: 0.82rem; font-weight: 500; color: var(--text-secondary); }
.form-input {
  padding: 0.7rem 1rem;
  background: rgba(255,255,255,0.04); border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  color: var(--text-primary); font-size: 0.9rem; font-family: inherit;
  transition: var(--transition); outline: none;
}
.form-input::placeholder { color: var(--text-muted); }
.form-input:focus { border-color: var(--accent); box-shadow: 0 0 0 3px rgba(99,102,241,0.12); }
.form-input.error { border-color: #ef4444; }
.form-textarea { resize: vertical; min-height: 120px; }
.form-error { font-size: 0.75rem; color: #ef4444; }
.form-success {
  display: flex; align-items: center; gap: 0.5rem;
  padding: 0.75rem 1rem; margin-top: 1rem;
  background: rgba(34,197,94,0.1); border: 1px solid rgba(34,197,94,0.3);
  border-radius: var(--radius-sm); color: #86efac; font-size: 0.875rem;
}

@media (max-width: 992px) { .contact-layout { grid-template-columns: 1fr; } }
@media (max-width: 600px) { .form-row { grid-template-columns: 1fr; } }
</style>
