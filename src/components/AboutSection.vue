<template>
  <section id="about" class="section-padding">
    <div class="container">
      <div class="about-inner">
        <!-- Left: Image + extras -->
        <div class="about-left reveal-left">

          <!-- Profile frame -->
          <div class="profile-frame-wrap">
            <!-- Corner accents -->
            <span class="corner corner-tl"></span>
            <span class="corner corner-tr"></span>
            <span class="corner corner-bl"></span>
            <span class="corner corner-br"></span>

            <div class="about-image">
              <img src="../assets/heandet.jpg" alt="Hean Det" class="about-photo" />
              <!-- Overlay name card -->
              <div class="photo-name-card">
                <span class="photo-name">Hean Det</span>
                <span class="photo-role mono">Web &amp; Software Dev</span>
              </div>
            </div>

            <!-- Floating badges -->
            <div class="float-badge float-badge-top">
              <span class="badge-dot-green pulse-dot"></span>
              <span class="mono" style="font-size:0.72rem">Open to work</span>
            </div>
            <div class="float-badge float-badge-side">
              <span style="font-size:1.1rem">🇰🇭</span>
              <span class="mono" style="font-size:0.72rem">Cambodia</span>
            </div>
            <div class="float-badge float-badge-bottom">
              <span style="font-size:1rem">💻</span>
              <span class="mono" style="font-size:0.72rem">3+ yrs coding</span>
            </div>
          </div>

          <!-- Social links -->
          <div class="social-links">
            <a href="https://github.com/heandet1676" target="_blank" class="social-btn" aria-label="GitHub">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.3 3.44 9.8 8.2 11.38.6.11.82-.26.82-.58v-2.03c-3.34.73-4.04-1.6-4.04-1.6-.55-1.38-1.33-1.75-1.33-1.75-1.09-.74.08-.73.08-.73 1.2.08 1.84 1.24 1.84 1.24 1.07 1.83 2.8 1.3 3.48 1 .11-.78.42-1.3.76-1.6-2.67-.3-5.47-1.33-5.47-5.93 0-1.31.47-2.38 1.24-3.22-.14-.3-.54-1.52.1-3.18 0 0 1.01-.32 3.3 1.23a11.5 11.5 0 0 1 3-.4c1.02 0 2.04.13 3 .4 2.28-1.55 3.29-1.23 3.29-1.23.64 1.66.24 2.88.12 3.18.77.84 1.23 1.91 1.23 3.22 0 4.61-2.81 5.63-5.48 5.92.43.37.81 1.1.81 2.22v3.29c0 .32.21.7.82.58C20.56 21.8 24 17.3 24 12c0-6.63-5.37-12-12-12z"/></svg>
              GitHub
            </a>
            <a href="mailto:heandet1676@gmail.com" class="social-btn" aria-label="Email">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
              Email
            </a>
            <a href="#" class="social-btn" aria-label="LinkedIn">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M20.45 20.45h-3.56v-5.57c0-1.33-.03-3.04-1.85-3.04-1.85 0-2.14 1.45-2.14 2.94v5.67H9.34V9h3.41v1.56h.05c.48-.9 1.64-1.85 3.37-1.85 3.6 0 4.27 2.37 4.27 5.45v6.29zM5.34 7.43a2.07 2.07 0 1 1 0-4.14 2.07 2.07 0 0 1 0 4.14zM6.9 20.45H3.76V9H6.9v11.45zM22.22 0H1.77C.79 0 0 .77 0 1.73v20.54C0 23.23.79 24 1.77 24h20.45c.98 0 1.78-.77 1.78-1.73V1.73C24 .77 23.2 0 22.22 0z"/></svg>
              LinkedIn
            </a>
          </div>

          <!-- Stats grid -->
          <div class="stats-grid">
            <div class="stat-card glass-card" v-for="(stat, i) in stats" :key="stat.label" :style="{animationDelay: (i*0.1)+'s'}">
              <div class="stat-number gradient-text">{{ stat.value }}</div>
              <div class="stat-label">{{ stat.label }}</div>
            </div>
          </div>
        </div>

        <!-- Right: Text -->
        <div class="about-right reveal-right" style="transition-delay:0.15s">
          <span class="section-label">About Me</span>
          <h2 class="section-title">Passionate about<br><span class="gradient-text">Building the Web</span></h2>
          <div class="section-divider"></div>

          <!-- Typewriter role ticker -->
          <div class="role-ticker">
            <span class="ticker-prefix mono">role =&gt;</span>
            <span class="ticker-text mono" :key="currentRole">{{ currentRole }}</span>
            <span class="ticker-cursor">|</span>
          </div>

          <p class="about-para">
            I'm <strong>Hean Det</strong>, a young web developer and software developer based in
            <strong>Cambodia</strong>. I am passionate about crafting clean, performant, and
            user-focused digital experiences that solve real problems.
          </p>
          <p class="about-para">
            My interests span <strong>web development</strong>, <strong>software development</strong>,
            <strong>UI/UX design</strong>, <strong>database systems</strong>, and modern technologies.
            I enjoy building practical products that combine elegant design with reliable engineering.
          </p>

          <!-- Info grid -->
          <div class="info-grid">
            <div class="info-item" v-for="info in infoItems" :key="info.label">
              <span class="info-icon" v-html="info.icon"></span>
              <div>
                <div class="info-label mono">{{ info.label }}</div>
                <div class="info-value">{{ info.value }}</div>
              </div>
            </div>
          </div>

          <!-- Interest tags -->
          <div class="interest-tags">
            <span class="interest-tag" v-for="tag in interests" :key="tag">{{ tag }}</span>
          </div>

          <!-- Actions -->
          <div class="about-actions">
            <a href="#" class="btn-primary-custom">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
              Download Resume
            </a>
            <a href="#contact" class="btn-ghost-custom" @click.prevent="scrollTo('contact')">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>
              Let's Talk
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AboutSection',
  data() {
    return {
      stats: [
        { value: '10+', label: 'Projects Completed' },
        { value: '15+', label: 'Technologies' },
        { value: '3+',  label: 'Years Learning' },
        { value: '5+',  label: 'Happy Clients' }
      ],
      interests: [
        'Web Development', 'Software Development', 'UI/UX Design',
        'Database Systems', 'Mobile Apps', 'Open Source'
      ],
      infoItems: [
        {
          label: 'Location',
          value: 'Phnom Penh, Cambodia',
          icon: '<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>'
        },
        {
          label: 'Email',
          value: 'heandet1676@gmail.com',
          icon: '<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>'
        },
        {
          label: 'Languages',
          value: 'Khmer (Native), English (Conversational)',
          icon: '<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>'
        },
        {
          label: 'Availability',
          value: 'Full-time / Freelance',
          icon: '<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>'
        }
      ],
      roles: ['Web Developer', 'Software Developer', 'UI/UX Enthusiast', 'Flutter Developer', 'Open Source Contributor'],
      currentRole: 'Web Developer',
      roleIndex: 0,
      roleInterval: null
    }
  },
  mounted() {
    this.roleInterval = setInterval(() => {
      this.roleIndex = (this.roleIndex + 1) % this.roles.length
      this.currentRole = this.roles[this.roleIndex]
    }, 2800)
  },
  beforeUnmount() {
    clearInterval(this.roleInterval)
  },
  methods: {
    scrollTo(id) {
      document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
    }
  }
}
</script>

<style scoped>
.about-inner {
  display: grid; grid-template-columns: 1fr 1.5fr; gap: 5rem; align-items: center;
}

/* ---- Profile frame ---- */
.profile-frame-wrap {
  position: relative;
  max-width: 340px;
  margin: 0 auto;
}
.corner {
  position: absolute;
  width: 22px; height: 22px;
  border-color: var(--accent-light);
  border-style: solid;
  z-index: 2;
}
.corner-tl { top: -8px; left: -8px; border-width: 2px 0 0 2px; border-radius: 4px 0 0 0; }
.corner-tr { top: -8px; right: -8px; border-width: 2px 2px 0 0; border-radius: 0 4px 0 0; }
.corner-bl { bottom: -8px; left: -8px; border-width: 0 0 2px 2px; border-radius: 0 0 0 4px; }
.corner-br { bottom: -8px; right: -8px; border-width: 0 2px 2px 0; border-radius: 0 0 4px 0; }

.about-image {
  width: 100%; aspect-ratio: 3/4;
  border-radius: var(--radius-xl);
  background: var(--bg-card);
  border: 1px solid var(--border);
  overflow: hidden;
  position: relative;
  box-shadow: 0 40px 80px rgba(0,0,0,0.5), 0 0 0 1px rgba(99,102,241,0.15);
  transition: box-shadow 0.4s ease;
}
.about-image:hover {
  box-shadow: 0 40px 100px rgba(0,0,0,0.6), 0 0 40px rgba(99,102,241,0.25);
}
.about-image::before {
  content: '';
  position: absolute; inset: 0; z-index: 1;
  background: linear-gradient(135deg, rgba(99,102,241,0.12) 0%, rgba(6,182,212,0.08) 100%);
}
.about-photo {
  width: 100%; height: 100%;
  object-fit: cover; object-position: center top;
  display: block;
  transition: transform 0.6s cubic-bezier(0.4,0,0.2,1);
}
.about-image:hover .about-photo { transform: scale(1.06); }

/* Name card overlay at bottom of photo */
.photo-name-card {
  position: absolute; bottom: 0; left: 0; right: 0; z-index: 2;
  padding: 1.5rem 1.2rem 1rem;
  background: linear-gradient(to top, rgba(10,10,15,0.95) 0%, transparent 100%);
  display: flex; flex-direction: column; gap: 2px;
  transform: translateY(4px);
  transition: transform 0.4s ease;
}
.about-image:hover .photo-name-card { transform: translateY(0); }
.photo-name { font-size: 1.15rem; font-weight: 700; color: #f8fafc; }
.photo-role { font-size: 0.72rem; color: var(--accent-light); letter-spacing: 0.08em; }

/* Floating badges around photo */
.float-badge {
  position: absolute;
  background: rgba(10,10,20,0.92); border: 1px solid rgba(99,102,241,0.25);
  border-radius: 50px; padding: 0.35rem 0.8rem;
  display: flex; align-items: center; gap: 0.4rem;
  backdrop-filter: blur(10px);
  white-space: nowrap;
  z-index: 3;
  animation: float 3.5s ease-in-out infinite;
}
.float-badge-top    { top: 12px; right: -20px; animation-duration: 3.5s; }
.float-badge-side   { bottom: 40%; left: -20px; animation-duration: 4s; animation-delay: 0.5s; }
.float-badge-bottom { bottom: -16px; right: 20px; animation-duration: 4.5s; animation-delay: 1s; }

.pulse-dot {
  width: 7px; height: 7px; border-radius: 50%; background: #22c55e;
  box-shadow: 0 0 0 3px rgba(34,197,94,0.25);
  animation: pulse-glow 2s ease-in-out infinite;
}

/* ---- Social links ---- */
.social-links {
  display: flex; gap: 0.75rem; justify-content: center; flex-wrap: wrap;
  margin-top: 1.5rem;
}
.social-btn {
  display: inline-flex; align-items: center; gap: 0.4rem;
  padding: 0.45rem 1rem;
  background: rgba(255,255,255,0.04);
  border: 1px solid var(--border);
  border-radius: 50px;
  font-size: 0.8rem; font-weight: 500;
  color: var(--text-secondary); text-decoration: none;
  transition: all 0.3s ease;
}
.social-btn:hover {
  border-color: var(--accent-light);
  color: var(--accent-light);
  background: rgba(99,102,241,0.08);
  transform: translateY(-2px);
  box-shadow: 0 4px 16px rgba(99,102,241,0.2);
}

/* ---- Stats grid ---- */
.stats-grid {
  display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;
  max-width: 340px; margin: 1.5rem auto 0;
}
.stat-card {
  padding: 1.25rem; text-align: center; border-radius: var(--radius-md);
  animation: count-up 0.6s ease both;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.stat-card:hover {
  transform: translateY(-6px) scale(1.04);
  box-shadow: 0 12px 40px rgba(99,102,241,0.25);
}
.stat-number { font-size: 2rem; font-weight: 800; letter-spacing: -0.02em; line-height: 1; margin-bottom: 0.25rem; }
.stat-label  { font-size: 0.8rem; color: var(--text-secondary); line-height: 1.3; }

/* ---- Right side ---- */
.role-ticker {
  display: flex; align-items: center; gap: 0.5rem;
  background: rgba(99,102,241,0.06); border: 1px solid rgba(99,102,241,0.18);
  border-radius: var(--radius-sm); padding: 0.5rem 1rem;
  margin-bottom: 1.5rem; width: fit-content;
}
.ticker-prefix { font-size: 0.8rem; color: var(--text-muted); }
.ticker-text {
  font-size: 0.85rem; color: var(--accent-light);
  animation: ticker-fade 0.4s ease both;
}
@keyframes ticker-fade {
  from { opacity: 0; transform: translateY(6px); }
  to   { opacity: 1; transform: translateY(0); }
}
.ticker-cursor {
  color: var(--accent-light);
  animation: blink-cur 1s step-end infinite;
  font-weight: 300;
}
@keyframes blink-cur { 0%,100%{opacity:1} 50%{opacity:0} }

.about-para {
  color: var(--text-secondary); line-height: 1.85; margin-bottom: 1rem; font-size: 0.97rem;
}
.about-para strong { color: var(--text-primary); font-weight: 600; }

/* Info grid */
.info-grid {
  display: grid; grid-template-columns: 1fr 1fr; gap: 0.85rem;
  margin: 1.5rem 0;
}
.info-item {
  display: flex; align-items: flex-start; gap: 0.6rem;
  padding: 0.75rem; border-radius: var(--radius-sm);
  background: rgba(255,255,255,0.02); border: 1px solid var(--border);
  transition: border-color 0.3s ease, background 0.3s ease;
}
.info-item:hover { border-color: rgba(99,102,241,0.3); background: rgba(99,102,241,0.05); }
.info-icon { color: var(--accent-light); flex-shrink: 0; margin-top: 2px; }
.info-label { font-size: 0.68rem; color: var(--text-muted); letter-spacing: 0.08em; text-transform: uppercase; margin-bottom: 2px; }
.info-value { font-size: 0.82rem; color: var(--text-secondary); font-weight: 500; }

/* Interest tags */
.interest-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 0.5rem; }
.interest-tag {
  padding: 0.35rem 0.9rem;
  background: rgba(99,102,241,0.08); border: 1px solid rgba(99,102,241,0.2);
  border-radius: 50px; font-size: 0.82rem; color: var(--accent-light);
}

/* Actions */
.about-actions { display: flex; gap: 1rem; flex-wrap: wrap; margin-top: 1.75rem; }

@keyframes count-up {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}

@media (max-width: 992px) {
  .about-inner { grid-template-columns: 1fr; gap: 3rem; }
  .float-badge-top  { right: -10px; }
  .float-badge-side { left: -10px; }
  .info-grid { grid-template-columns: 1fr; }
}
@media (max-width: 480px) {
  .about-actions { flex-direction: column; }
}
</style>
