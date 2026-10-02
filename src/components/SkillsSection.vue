<template>
  <section id="skills" class="section-padding" style="background:var(--bg-secondary)">
    <div class="container">
      <div class="text-center mb-5 reveal">
        <span class="section-label">What I Know</span>
        <h2 class="section-title">Skills & <span class="gradient-text">Technologies</span></h2>
        <div class="section-divider mx-auto"></div>
        <p class="section-subtitle mx-auto">A curated set of tools and technologies I use to build modern digital products.</p>
      </div>

      <div class="skills-grid">
        <div class="skill-category glass-card reveal-scale" v-for="(cat, idx) in categories" :key="cat.name" :style="{ transitionDelay: (idx * 0.1) + 's' }">
          <div class="cat-header">
            <div class="cat-icon" v-html="cat.icon"></div>
            <h3 class="cat-name">{{ cat.name }}</h3>
          </div>
          <div class="skills-list">
            <div class="skill-item" v-for="skill in cat.skills" :key="skill.name">
              <div class="skill-info">
                <img v-if="skill.icon" :src="skill.icon" :alt="skill.name" class="skill-img" width="20" height="20" />
                <span class="skill-name">{{ skill.name }}</span>
              </div>
              <div class="skill-bar-wrap">
                <div class="skill-bar" :style="{ width: skill.level + '%' }"></div>
              </div>
              <span class="skill-level mono">{{ skill.label }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Tech badges row -->
      <div class="tech-badges reveal mt-5">
        <h4 class="badges-title">Also familiar with</h4>
        <div class="badges-row">
          <span class="tech-badge scroll-animate" v-for="t in extraTech" :key="t">{{ t }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
const DEV = 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/'
export default {
  name: 'SkillsSection',
  data() {
    return {
      categories: [
        {
          name: 'Frontend',
          icon: '<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>',
          skills: [
            { name: 'HTML5',               icon: DEV + 'html5/html5-original.svg',       level: 90, label: 'Advanced' },
            { name: 'CSS3',                icon: DEV + 'css3/css3-original.svg',          level: 85, label: 'Advanced' },
            { name: 'JavaScript',          icon: DEV + 'javascript/javascript-original.svg', level: 80, label: 'Proficient' },
            { name: 'Vue.js',              icon: DEV + 'vuejs/vuejs-original.svg',        level: 78, label: 'Proficient' },
            { name: 'Bootstrap',           icon: DEV + 'bootstrap/bootstrap-original.svg',level: 85, label: 'Advanced' },
            { name: 'Responsive Design',   icon: null,                                    level: 88, label: 'Advanced' }
          ]
        },
        {
          name: 'Backend & Database',
          icon: '<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/></svg>',
          skills: [
            { name: 'Node.js',   icon: DEV + 'nodejs/nodejs-original.svg',      level: 72, label: 'Proficient' },
            { name: 'REST API',  icon: null,                                      level: 75, label: 'Proficient' },
            { name: 'Supabase', icon: null,                                       level: 78, label: 'Proficient' },
            { name: 'Firebase', icon: DEV + 'firebase/firebase-plain.svg',       level: 75, label: 'Proficient' },
            { name: 'SQL',      icon: null,                                       level: 70, label: 'Comfortable' }
          ]
        },
        {
          name: 'Programming',
          icon: '<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"/><line x1="3" y1="9" x2="21" y2="9"/><line x1="9" y1="21" x2="9" y2="9"/></svg>',
          skills: [
            { name: 'JavaScript', icon: DEV + 'javascript/javascript-original.svg', level: 80, label: 'Proficient' },
            { name: 'Dart',       icon: DEV + 'dart/dart-original.svg',             level: 72, label: 'Proficient' },
            { name: 'Flutter',    icon: DEV + 'flutter/flutter-original.svg',       level: 70, label: 'Comfortable' }
          ]
        },
        {
          name: 'Tools & Workflow',
          icon: '<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="3"/><path d="M19.07 4.93A10 10 0 0 0 4.93 19.07M4.93 4.93A10 10 0 0 0 19.07 19.07"/></svg>',
          skills: [
            { name: 'Git',     icon: DEV + 'git/git-original.svg',                      level: 80, label: 'Proficient' },
            { name: 'GitHub',  icon: null,                                               level: 82, label: 'Proficient' },
            { name: 'VS Code', icon: DEV + 'vscode/vscode-original.svg',                level: 90, label: 'Advanced' },
            { name: 'Figma',   icon: DEV + 'figma/figma-original.svg',                  level: 65, label: 'Comfortable' },
            { name: 'Netlify', icon: null,                                               level: 70, label: 'Comfortable' }
          ]
        }
      ],
      extraTech: ['Tailwind CSS', 'Vite', 'npm', 'Postman', 'Linux', 'SCSS', 'JSON', 'Markdown']
    }
  }
}
</script>

<style scoped>
.skills-grid {
  display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem;
}
.skill-category { padding: 2rem; }
.cat-header { display: flex; align-items: center; gap: 0.75rem; margin-bottom: 1.75rem; }
.cat-icon {
  width: 40px; height: 40px;
  background: rgba(99,102,241,0.1); border: 1px solid rgba(99,102,241,0.2);
  border-radius: var(--radius-sm);
  display: flex; align-items: center; justify-content: center;
  color: var(--accent-light);
}
.cat-name { font-size: 1.05rem; font-weight: 700; margin: 0; }
.skills-list { display: flex; flex-direction: column; gap: 1rem; }
.skill-item { display: grid; grid-template-columns: 1fr auto auto; align-items: center; gap: 0.75rem; }
.skill-info { display: flex; align-items: center; gap: 0.5rem; }
.skill-img { object-fit: contain; }
.skill-name { font-size: 0.88rem; font-weight: 500; color: var(--text-secondary); white-space: nowrap; }
.skill-bar-wrap { width: 80px; height: 4px; background: rgba(255,255,255,0.07); border-radius: 2px; overflow: hidden; }
.skill-bar {
  height: 100%;
  background: linear-gradient(90deg, #6366f1 0%, #06b6d4 60%, #a855f7 100%);
  background-size: 200% auto;
  border-radius: 2px;
  transition: width 1.2s cubic-bezier(0.4,0,0.2,1);
  animation: bar-shimmer 2.5s linear infinite;
  box-shadow: 0 0 8px rgba(99,102,241,0.4);
}
.skill-bar-wrap:hover .skill-bar {
  box-shadow: 0 0 14px rgba(99,102,241,0.7);
}
.skill-level { font-size: 0.7rem; color: var(--text-muted); font-family: var(--font-mono); white-space: nowrap; }

/* Extra badges */
.tech-badges { text-align: center; }
.badges-title { font-size: 0.875rem; color: var(--text-secondary); font-weight: 500; margin-bottom: 1rem; }
.badges-row { display: flex; flex-wrap: wrap; gap: 0.5rem; justify-content: center; }
.tech-badge {
  padding: 0.35rem 0.9rem;
  background: var(--bg-card); border: 1px solid var(--border);
  border-radius: 50px; font-size: 0.8rem; color: var(--text-secondary);
  font-family: var(--font-mono); transition: var(--transition);
}
.tech-badge:hover { border-color: var(--border-accent); color: var(--accent-light); }

@media (max-width: 768px) {
  .skills-grid { grid-template-columns: 1fr; }
  .skill-item { grid-template-columns: 1fr; gap: 0.35rem; }
  .skill-bar-wrap { width: 100%; }
}
</style>

