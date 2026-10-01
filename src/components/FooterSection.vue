<template>
  <footer class="footer-section">
    <div class="footer-glow"></div>
    <div class="container">
      <div class="footer-inner">
        <!-- Brand -->
        <div class="footer-brand">
          <a href="#home" class="footer-logo" @click.prevent="scrollTop">
            <span class="logo-bracket mono">&lt;</span>
            <span style="color:var(--text-primary)">HD</span>
            <span class="logo-bracket mono">/&gt;</span>
          </a>
          <p class="footer-tagline">Web Developer &amp; Software Developer</p>
          <p class="footer-desc">Building modern, responsive, and user-focused web applications with clean design and reliable technology.</p>
          <div class="footer-socials">
            <a v-for="social in socials" :key="social.name" :href="social.url" target="_blank" rel="noopener" :aria-label="social.name" class="footer-social-btn" v-html="social.icon"></a>
          </div>
        </div>

        <!-- Nav links -->
        <div class="footer-nav">
          <p class="footer-nav-title">Navigation</p>
          <ul>
            <li v-for="link in navLinks" :key="link.id">
              <a :href="'#' + link.id" @click.prevent="scrollTo(link.id)">{{ link.label }}</a>
            </li>
          </ul>
        </div>

        <!-- Services links -->
        <div class="footer-nav">
          <p class="footer-nav-title">Services</p>
          <ul>
            <li v-for="s in services" :key="s"><a href="#">{{ s }}</a></li>
          </ul>
        </div>

        <!-- Contact snippet -->
        <div class="footer-contact">
          <p class="footer-nav-title">Get In Touch</p>
          <div class="footer-contact-item">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
            <span>heandet1676@gmail.com</span>
          </div>
          <div class="footer-contact-item">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
            <span>Battambang, Cambodia</span>
          </div>
          <a href="#contact" class="btn-primary-custom mt-3" style="font-size:0.82rem;padding:0.55rem 1.2rem" @click.prevent="scrollTo('contact')">Start a Project</a>
        </div>
      </div>

      <div class="footer-bottom">
        <p class="footer-copy mono">© 2026 Hean Det. All rights reserved.</p>
        <p class="footer-made">Crafted with Vue.js &amp; Bootstrap 5</p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterSection',
  data() {
    return {
      navLinks: [
        { id: 'home',       label: 'Home' },
        { id: 'about',      label: 'About' },
        { id: 'skills',     label: 'Skills' },
        { id: 'projects',   label: 'Projects' },
        { id: 'experience', label: 'Experience' },
        { id: 'education',  label: 'Education' },
        { id: 'contact',    label: 'Contact' }
      ],
      services: ['Web Development', 'Responsive Design', 'UI/UX Implementation', 'E-commerce', 'API Integration', 'Mobile Apps'],
      socials: [
        {
          name: 'GitHub',
          url: 'https://github.com/heandet',
          icon: '<svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>'
        },
        {
          name: 'LinkedIn',
          url: 'https://linkedin.com/in/heandet',
          icon: '<svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>'
        },
        {
          name: 'Facebook',
          url: 'https://facebook.com/heandet',
          icon: '<svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>'
        }
      ]
    }
  },
  methods: {
    scrollTo(id) { document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' }) },
    scrollTop() { window.scrollTo({ top: 0, behavior: 'smooth' }) }
  }
}
</script>

<style scoped>
.footer-section {
  position: relative; overflow: hidden;
  background: var(--bg-primary);
  border-top: 1px solid var(--border);
  padding: 5rem 0 2rem;
}
.footer-glow {
  position: absolute; top: 0; left: 50%; transform: translateX(-50%);
  width: 600px; height: 300px;
  background: radial-gradient(ellipse at top, rgba(99,102,241,0.1) 0%, transparent 70%);
  pointer-events: none;
}
.footer-inner {
  display: grid; grid-template-columns: 2fr 1fr 1fr 1.5fr; gap: 3rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid var(--border);
}
.footer-logo {
  font-family: var(--font-mono); font-size: 1.4rem; font-weight: 700;
  text-decoration: none; display: inline-flex; align-items: center; gap: 2px;
  margin-bottom: 0.75rem;
}
.logo-bracket { color: var(--accent-light); }
.footer-tagline { font-size: 0.875rem; color: var(--text-secondary); margin-bottom: 0.75rem; font-weight: 500; }
.footer-desc { font-size: 0.82rem; color: var(--text-muted); line-height: 1.7; margin-bottom: 1.5rem; max-width: 280px; }
.footer-socials { display: flex; gap: 0.6rem; }
.footer-social-btn {
  width: 36px; height: 36px;
  background: rgba(255,255,255,0.04); border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  display: flex; align-items: center; justify-content: center;
  color: var(--text-secondary); text-decoration: none;
  transition: var(--transition);
}
.footer-social-btn:hover { border-color: var(--border-accent); color: var(--accent-light); background: rgba(99,102,241,0.08); }
.footer-nav-title { font-size: 0.8rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.1em; color: var(--text-primary); margin-bottom: 1.25rem; }
.footer-nav ul { list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 0.6rem; }
.footer-nav a { font-size: 0.875rem; color: var(--text-secondary); text-decoration: none; transition: color 0.2s ease; }
.footer-nav a:hover { color: var(--accent-light); }
.footer-contact-item { display: flex; align-items: center; gap: 0.5rem; font-size: 0.82rem; color: var(--text-secondary); margin-bottom: 0.5rem; }
.footer-bottom { display: flex; justify-content: space-between; align-items: center; padding-top: 1.5rem; flex-wrap: wrap; gap: 0.5rem; }
.footer-copy, .footer-made { font-size: 0.78rem; color: var(--text-muted); margin: 0; }

@media (max-width: 1100px) { .footer-inner { grid-template-columns: 1fr 1fr; } }
@media (max-width: 640px)  { .footer-inner { grid-template-columns: 1fr; gap: 2rem; } .footer-bottom { flex-direction: column; text-align: center; } }
</style>
