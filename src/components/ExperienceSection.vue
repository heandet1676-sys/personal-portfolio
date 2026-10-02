<template>
  <section id="experience" class="section-padding" style="background:var(--bg-secondary)">
    <div class="container">
      <div class="text-center mb-5 reveal">
        <span class="section-label">Journey</span>
        <h2 class="section-title">Work <span class="gradient-text">Experience</span></h2>
        <div class="section-divider mx-auto"></div>
      </div>

      <div class="timeline">
        <div class="timeline-item reveal-left" v-for="(exp, idx) in experiences" :key="idx" :style="{ transitionDelay: (idx * 0.12) + 's' }">
          <div class="timeline-dot" :class="exp.current ? 'dot-active' : ''">
            <div class="dot-inner"></div>
          </div>
          <div class="timeline-line" v-if="idx < experiences.length - 1"></div>
          <div class="timeline-content glass-card">
            <div class="exp-header">
              <div>
                <span class="exp-current mono" v-if="exp.current">Current</span>
                <h3 class="exp-title">{{ exp.position }}</h3>
                <p class="exp-company">{{ exp.company }}</p>
              </div>
              <div class="exp-date mono">{{ exp.period }}</div>
            </div>
            <p class="exp-desc">{{ exp.description }}</p>
            <div class="exp-tech">
              <span class="tech-tag" v-for="tech in exp.technologies" :key="tech">{{ tech }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ExperienceSection',
  data() {
    return {
      experiences: [
        {
          position: 'Freelance Web Developer',
          company: 'Self-Employed — Remote',
          period: '2024 – Present',
          current: true,
          description: 'Building and delivering custom web applications for clients. Responsibilities include requirements gathering, UI/UX design, full-stack development, database setup, and deployment. Working with Vue.js, Supabase, Firebase, and Bootstrap.',
          technologies: ['Vue.js', 'Supabase', 'Firebase', 'Bootstrap', 'Node.js']
        },
        {
          position: 'Junior Web Developer',
          company: 'Personal Projects & Academic Work',
          period: '2023 – 2024',
          current: false,
          description: 'Developed multiple full-stack web projects including e-commerce platforms and streaming services. Focused on learning modern JavaScript frameworks, RESTful API design, and database integration.',
          technologies: ['Vue.js', 'JavaScript', 'REST API', 'SQL', 'Git']
        },
        {
          position: 'Flutter Mobile Developer',
          company: 'Personal & Academic Projects',
          period: '2023',
          current: false,
          description: 'Built cross-platform mobile applications using Flutter and Dart. Integrated Firebase for authentication and real-time database functionality. Learned state management and responsive mobile UI design.',
          technologies: ['Flutter', 'Dart', 'Firebase', 'Android', 'iOS']
        }
      ]
    }
  }
}
</script>

<style scoped>
.timeline { position: relative; max-width: 800px; margin: 0 auto; }
.timeline-item { display: grid; grid-template-columns: 40px 1fr; gap: 0 1.5rem; position: relative; padding-bottom: 2rem; }
.timeline-dot {
  width: 40px; height: 40px; border-radius: 50%;
  background: var(--bg-secondary); border: 2px solid var(--border);
  display: flex; align-items: center; justify-content: center;
  position: relative; z-index: 1; flex-shrink: 0;
  transition: var(--transition);
}
.timeline-dot.dot-active { border-color: var(--accent); box-shadow: 0 0 0 4px rgba(99,102,241,0.15); }
.dot-inner { width: 12px; height: 12px; border-radius: 50%; background: var(--border); }
.dot-active .dot-inner { background: var(--accent); }
.timeline-line {
  position: absolute; left: 20px; top: 40px; bottom: 0; width: 1px;
  background: linear-gradient(to bottom, var(--border) 0%, transparent 100%);
}
.timeline-content { padding: 1.5rem; border-radius: var(--radius-lg); }
.exp-header { display: flex; justify-content: space-between; align-items: flex-start; gap: 1rem; margin-bottom: 0.75rem; flex-wrap: wrap; }
.exp-current {
  display: inline-block; font-size: 0.7rem; color: var(--accent-light);
  padding: 0.15rem 0.6rem; background: rgba(99,102,241,0.12); border: 1px solid rgba(99,102,241,0.25);
  border-radius: 50px; margin-bottom: 0.4rem;
}
.exp-title { font-size: 1.05rem; font-weight: 700; margin-bottom: 0.15rem; }
.exp-company { font-size: 0.875rem; color: var(--text-secondary); margin: 0; }
.exp-date { font-size: 0.78rem; color: var(--text-muted); white-space: nowrap; }
.exp-desc { font-size: 0.875rem; color: var(--text-secondary); line-height: 1.7; margin-bottom: 1rem; }
.exp-tech { display: flex; gap: 0.4rem; flex-wrap: wrap; }
.tech-tag {
  padding: 0.2rem 0.6rem;
  background: rgba(255,255,255,0.04); border: 1px solid var(--border);
  border-radius: 50px; font-size: 0.72rem; color: var(--text-muted); font-family: var(--font-mono);
}

@media (max-width: 600px) {
  .timeline-item { grid-template-columns: 30px 1fr; }
  .timeline-dot { width: 30px; height: 30px; }
  .exp-header { flex-direction: column; }
}
</style>

