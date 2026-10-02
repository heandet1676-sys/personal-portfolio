<template>
  <section id="projects" class="section-padding">
    <div class="container">
      <div class="text-center mb-5 reveal">
        <span class="section-label">Featured Work</span>
        <h2 class="section-title">Selected <span class="gradient-text">Projects</span></h2>
        <div class="section-divider mx-auto"></div>
        <p class="section-subtitle mx-auto">A collection of projects I have built — from web platforms to mobile applications.</p>
      </div>

      <!-- Filter tabs -->
      <div class="filter-tabs reveal mb-5">
        <button v-for="tab in tabs" :key="tab" class="filter-btn" :class="{ active: activeTab === tab }" @click="activeTab = tab">{{ tab }}</button>
      </div>

      <div class="projects-grid">
        <div class="project-card glass-card scroll-animate" v-for="(proj, idx) in filteredProjects" :key="proj.id" :style="{ transitionDelay: (idx * 0.1) + 's' }">
          <!-- Project image -->
          <div class="proj-image" :style="{ background: proj.gradient }">
            <div class="proj-image-inner">
              <div class="proj-mockup">
                <div class="mockup-bar">
                  <span></span><span></span><span></span>
                </div>
                <div class="mockup-body" v-html="proj.visual"></div>
              </div>
            </div>
            <div class="proj-category mono">{{ proj.category }}</div>
          </div>

          <!-- Project info -->
          <div class="proj-body">
            <h3 class="proj-title">{{ proj.name }}</h3>
            <p class="proj-desc">{{ proj.description }}</p>

            <!-- Features -->
            <div class="proj-features">
              <span class="feature-dot" v-for="feat in proj.features.slice(0,3)" :key="feat">{{ feat }}</span>
            </div>

            <!-- Technologies -->
            <div class="proj-tech">
              <span class="tech-tag" v-for="tech in proj.technologies" :key="tech">{{ tech }}</span>
            </div>

            <!-- Actions -->
            <div class="proj-actions">
              <a :href="proj.demo" class="btn-primary-custom btn-sm-proj" target="_blank" rel="noopener">
                <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
                Live Demo
              </a>
              <a :href="proj.github" class="btn-ghost-custom btn-sm-proj" target="_blank" rel="noopener">
                <svg width="15" height="15" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
                GitHub
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- CTA -->
      <div class="text-center mt-5 reveal">
        <a href="https://github.com/heandet" target="_blank" rel="noopener" class="btn-ghost-custom">
          View All Projects on GitHub
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="M12 5l7 7-7 7"/></svg>
        </a>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ProjectsSection',
  data() {
    return {
      activeTab: 'All',
      tabs: ['All', 'Web', 'Mobile'],
      projects: [
        {
          id: 1, category: 'Web Platform',
          name: 'Na Na Computer',
          description: 'A full-featured online computer retail and service management platform for managing products, orders, customers, and repair services.',
          technologies: ['Vue.js', 'Bootstrap', 'Supabase', 'Firebase'],
          features: ['Shopping Cart', 'Admin Dashboard', 'Service Management'],
          demo: '#', github: '#',
          gradient: 'linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%)',
          filter: 'Web',
          visual: '<div style="padding:1rem;font-family:monospace;font-size:0.65rem;color:#818cf8"><div style="color:#22c55e;margin-bottom:0.5rem">Na Na Computer</div><div style="color:#64748b">// Product Management System</div><div style="margin-top:0.5rem;color:#e2e8f0">orders: <span style="color:#a3e635">1,240</span></div><div style="color:#e2e8f0">products: <span style="color:#a3e635">380</span></div><div style="color:#e2e8f0">customers: <span style="color:#a3e635">560</span></div></div>'
        },
        {
          id: 2, category: 'Streaming Platform',
          name: 'MovieTime',
          description: 'A modern movie streaming platform with browsing, user accounts, video streaming via Bunny.net, and an integrated rental payment system.',
          technologies: ['Vue.js', 'Node.js', 'Supabase', 'Bunny.net'],
          features: ['Video Streaming', 'Rental System', 'User Accounts'],
          demo: '#', github: '#',
          gradient: 'linear-gradient(135deg, #0f0f1a 0%, #1a0a2e 50%, #2d1b69 100%)',
          filter: 'Web',
          visual: '<div style="padding:1rem;font-family:monospace;font-size:0.65rem;color:#818cf8"><div style="color:#a855f7;margin-bottom:0.5rem">MovieTime</div><div style="color:#64748b">// Streaming Platform</div><div style="margin-top:0.5rem;color:#e2e8f0">movies: <span style="color:#f59e0b">240+</span></div><div style="color:#e2e8f0">streaming: <span style="color:#22c55e">active</span></div><div style="color:#e2e8f0">users: <span style="color:#f59e0b">1.2k</span></div></div>'
        },
        {
          id: 3, category: 'Mobile App',
          name: 'Flutter Mobile Apps',
          description: 'Cross-platform mobile applications built with Flutter and Dart, leveraging Firebase for real-time data and authentication.',
          technologies: ['Flutter', 'Dart', 'Firebase'],
          features: ['Cross-Platform', 'Real-time Data', 'Authentication'],
          demo: '#', github: '#',
          gradient: 'linear-gradient(135deg, #0a1628 0%, #0e2040 50%, #054f7c 100%)',
          filter: 'Mobile',
          visual: '<div style="padding:1rem;font-family:monospace;font-size:0.65rem;color:#818cf8"><div style="color:#06b6d4;margin-bottom:0.5rem">Flutter App</div><div style="color:#64748b">// Mobile Development</div><div style="margin-top:0.5rem;color:#e2e8f0">platform: <span style="color:#06b6d4">iOS & Android</span></div><div style="color:#e2e8f0">state: <span style="color:#22c55e">production</span></div></div>'
        }
      ]
    }
  },
  computed: {
    filteredProjects() {
      if (this.activeTab === 'All') return this.projects
      return this.projects.filter(p => p.filter === this.activeTab)
    }
  }
}
</script>

<style scoped>
.filter-tabs { display: flex; gap: 0.5rem; justify-content: center; flex-wrap: wrap; }
.filter-btn {
  padding: 0.5rem 1.25rem;
  background: transparent; border: 1px solid var(--border);
  border-radius: 50px; color: var(--text-secondary);
  font-size: 0.875rem; font-weight: 500; cursor: pointer;
  transition: var(--transition);
}
.filter-btn.active, .filter-btn:hover { background: rgba(99,102,241,0.1); border-color: var(--border-accent); color: var(--accent-light); }

.projects-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; }
.project-card { padding: 0; overflow: hidden; cursor: default; }
.proj-image {
  height: 200px; position: relative; overflow: hidden;
  display: flex; align-items: center; justify-content: center;
}
.proj-image-inner { width: 100%; height: 100%; display: flex; align-items: center; justify-content: center; }
.proj-mockup {
  width: 80%; background: rgba(0,0,0,0.6); border-radius: 8px;
  border: 1px solid rgba(255,255,255,0.1); overflow: hidden;
}
.mockup-bar {
  padding: 0.4rem 0.75rem; background: rgba(255,255,255,0.05);
  display: flex; gap: 5px; align-items: center;
}
.mockup-bar span { width: 7px; height: 7px; border-radius: 50%; background: rgba(255,255,255,0.2); }
.mockup-bar span:nth-child(1) { background: #ff5f57; }
.mockup-bar span:nth-child(2) { background: #febc2e; }
.mockup-bar span:nth-child(3) { background: #28c840; }
.proj-category {
  position: absolute; top: 0.75rem; right: 0.75rem;
  padding: 0.2rem 0.65rem;
  background: rgba(0,0,0,0.6); border: 1px solid rgba(255,255,255,0.15);
  border-radius: 50px; font-size: 0.68rem; color: var(--text-secondary);
  backdrop-filter: blur(8px);
}
.proj-body { padding: 1.5rem; }
.proj-title { font-size: 1.15rem; font-weight: 700; margin-bottom: 0.6rem; }
.proj-desc { font-size: 0.875rem; color: var(--text-secondary); line-height: 1.7; margin-bottom: 1rem; }
.proj-features { display: flex; gap: 0.4rem; flex-wrap: wrap; margin-bottom: 1rem; }
.feature-dot {
  padding: 0.2rem 0.6rem;
  background: rgba(6,182,212,0.08); border: 1px solid rgba(6,182,212,0.2);
  border-radius: 50px; font-size: 0.72rem; color: var(--cyan);
}
.proj-tech { display: flex; gap: 0.4rem; flex-wrap: wrap; margin-bottom: 1.25rem; }
.tech-tag {
  padding: 0.2rem 0.6rem;
  background: rgba(255,255,255,0.04); border: 1px solid var(--border);
  border-radius: 50px; font-size: 0.72rem; color: var(--text-muted);
  font-family: var(--font-mono);
}
.proj-actions { display: flex; gap: 0.75rem; }
.btn-sm-proj { padding: 0.5rem 1rem; font-size: 0.82rem; }

@media (max-width: 1100px) { .projects-grid { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 640px) { .projects-grid { grid-template-columns: 1fr; } }
</style>

