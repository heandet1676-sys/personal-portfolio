<template>
  <section id="about" class="section-padding">
    <div class="container">
      <div class="about-inner">
        <!-- Left: Image + Stats -->
        <div class="about-left reveal">
          <div class="about-image-wrap">
            <div class="about-image">
              <img src="../assets/heandet.jpg" alt="Hean Det" class="about-photo" />
            </div>
            <div class="about-image-badge">
              <span class="badge-dot-green"></span>
              <span class="mono" style="font-size:0.75rem">Open to work</span>
            </div>
          </div>
          <!-- Stats grid -->
          <div class="stats-grid">
            <div class="stat-card glass-card" v-for="stat in stats" :key="stat.label">
              <div class="stat-number gradient-text">{{ stat.value }}</div>
              <div class="stat-label">{{ stat.label }}</div>
            </div>
          </div>
        </div>

        <!-- Right: Text -->
        <div class="about-right reveal" style="transition-delay:0.15s">
          <span class="section-label">About Me</span>
          <h2 class="section-title">Passionate about<br><span class="gradient-text">Building the Web</span></h2>
          <div class="section-divider"></div>
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
          <p class="about-para">
            I am continuously learning and growing, exploring full-stack web technologies, mobile
            development with Flutter, and scalable backend systems. I believe in writing code that
            is clean, maintainable, and meaningful.
          </p>

          <!-- Interest tags -->
          <div class="interest-tags">
            <span class="interest-tag" v-for="tag in interests" :key="tag">{{ tag }}</span>
          </div>

          <!-- Download CV -->
          <a href="#" class="btn-primary-custom mt-4">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
            Download Resume
          </a>
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
      ]
    }
  }
}
</script>

<style scoped>
.about-inner {
  display: grid; grid-template-columns: 1fr 1.4fr; gap: 5rem; align-items: center;
}
/* Left */
.about-left { display: flex; flex-direction: column; gap: 2rem; }
.about-image-wrap { position: relative; }
.about-image {
  width: 100%; aspect-ratio: 1;
  max-width: 340px; margin: 0 auto;
  border-radius: var(--radius-xl);
  background: var(--bg-card);
  border: 1px solid var(--border);
  overflow: hidden;
  display: flex; align-items: center; justify-content: center;
  position: relative;
  box-shadow: 0 40px 80px rgba(0,0,0,0.5), 0 0 0 1px rgba(99,102,241,0.1);
}
.about-img-placeholder { text-align: center; }
.about-photo { width: 100%; height: 100%; object-fit: cover; object-position: center top; display: block; }
.about-image::before {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(99,102,241,0.15) 0%, rgba(6,182,212,0.1) 100%);
}
.about-image-badge {
  position: absolute; bottom: -1rem; right: 1rem;
  background: rgba(15,15,26,0.95); border: 1px solid var(--border);
  border-radius: 50px; padding: 0.4rem 0.9rem;
  display: flex; align-items: center; gap: 0.5rem;
  backdrop-filter: blur(10px);
}
.badge-dot-green { width: 7px; height: 7px; border-radius: 50%; background: #22c55e; }

.stats-grid {
  display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; max-width: 340px; margin: 0 auto;
}
.stat-card { padding: 1.25rem; text-align: center; border-radius: var(--radius-md); }
.stat-number { font-size: 2rem; font-weight: 800; letter-spacing: -0.02em; line-height: 1; margin-bottom: 0.25rem; }
.stat-label { font-size: 0.8rem; color: var(--text-secondary); line-height: 1.3; }

/* Right */
.about-para {
  color: var(--text-secondary); line-height: 1.8; margin-bottom: 1rem; font-size: 0.97rem;
}
.about-para strong { color: var(--text-primary); font-weight: 600; }
.interest-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 1.5rem; }
.interest-tag {
  padding: 0.35rem 0.9rem;
  background: rgba(99,102,241,0.08); border: 1px solid rgba(99,102,241,0.2);
  border-radius: 50px; font-size: 0.82rem; color: var(--accent-light);
}

@media (max-width: 992px) {
  .about-inner { grid-template-columns: 1fr; gap: 3rem; }
}
</style>


