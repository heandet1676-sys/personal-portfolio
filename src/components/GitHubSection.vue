<template>
  <section id="github" class="section-padding">
    <div class="container">
      <div class="text-center mb-5 reveal">
        <span class="section-label">Open Source</span>
        <h2 class="section-title">GitHub <span class="gradient-text">Activity</span></h2>
        <div class="section-divider mx-auto"></div>
        <p class="section-subtitle mx-auto">Exploring code, building projects, and contributing to the developer community.</p>
      </div>

      <div class="github-layout">
        <!-- Stats cards -->
        <div class="github-stats reveal">
          <div class="stat-row">
            <div class="gh-stat-card glass-card" v-for="stat in ghStats" :key="stat.label">
              <div class="gh-stat-value gradient-text">{{ stat.value }}</div>
              <div class="gh-stat-label">{{ stat.label }}</div>
            </div>
          </div>

          <!-- Contribution grid visualization -->
          <div class="contribution-section glass-card reveal">
            <div class="contribution-header">
              <p class="contribution-title">Contribution Activity</p>
              <span class="mono" style="font-size:0.72rem;color:var(--text-muted)">Past 12 months</span>
            </div>
            <div class="contribution-grid">
              <div v-for="week in 52" :key="week" class="contrib-week">
                <div v-for="day in 7" :key="day" class="contrib-day" :class="getContribLevel(week, day)"></div>
              </div>
            </div>
            <div class="contrib-legend">
              <span style="font-size:0.72rem;color:var(--text-muted)">Less</span>
              <div class="legend-box l0"></div>
              <div class="legend-box l1"></div>
              <div class="legend-box l2"></div>
              <div class="legend-box l3"></div>
              <div class="legend-box l4"></div>
              <span style="font-size:0.72rem;color:var(--text-muted)">More</span>
            </div>
          </div>
        </div>

        <!-- Repos sidebar -->
        <div class="github-repos reveal" style="transition-delay:0.1s">
          <h3 class="repos-title">Featured Repositories</h3>
          <div class="repos-list">
            <div class="repo-card glass-card" v-for="repo in repos" :key="repo.name">
              <div class="repo-header">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color:var(--text-muted);flex-shrink:0"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"/></svg>
                <a href="#" class="repo-name">{{ repo.name }}</a>
                <span class="repo-visibility mono">{{ repo.visibility }}</span>
              </div>
              <p class="repo-desc">{{ repo.description }}</p>
              <div class="repo-meta">
                <span class="repo-lang"><span class="lang-dot" :style="{ background: repo.langColor }"></span>{{ repo.language }}</span>
                <span class="repo-stat mono">
                  <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor"><path d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z"/></svg>
                  {{ repo.stars }}
                </span>
              </div>
            </div>
          </div>

          <a href="https://github.com/heandet" target="_blank" rel="noopener" class="btn-primary-custom w-100 justify-content-center mt-4">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
            View GitHub Profile
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'GitHubSection',
  data() {
    return {
      ghStats: [
        { value: '20+', label: 'Repositories' },
        { value: '500+', label: 'Commits' },
        { value: '3+', label: 'Years Active' },
        { value: '10+', label: 'Projects' }
      ],
      repos: [
        { name: 'na-na-computer', description: 'Online computer retail and service management platform built with Vue.js and Supabase.', language: 'JavaScript', langColor: '#f1e05a', stars: 4, visibility: 'public' },
        { name: 'movietime-platform', description: 'Modern movie streaming platform with Vue.js and Bunny.net video streaming.', language: 'JavaScript', langColor: '#f1e05a', stars: 6, visibility: 'public' },
        { name: 'flutter-apps', description: 'Cross-platform mobile applications built with Flutter, Dart, and Firebase.', language: 'Dart', langColor: '#00b4ab', stars: 3, visibility: 'public' }
      ]
    }
  },
  methods: {
    getContribLevel(week, day) {
      // Generate a realistic-looking pseudorandom contribution pattern
      const seed = (week * 7 + day) * 2654435761
      const val = ((seed ^ (seed >> 16)) % 100 + 100) % 100
      if (val < 45) return 'l0'
      if (val < 62) return 'l1'
      if (val < 76) return 'l2'
      if (val < 89) return 'l3'
      return 'l4'
    }
  }
}
</script>

<style scoped>
.github-layout { display: grid; grid-template-columns: 1fr 320px; gap: 2rem; }
.stat-row { display: grid; grid-template-columns: repeat(4, 1fr); gap: 1rem; margin-bottom: 1.5rem; }
.gh-stat-card { padding: 1.25rem; text-align: center; border-radius: var(--radius-md); }
.gh-stat-value { font-size: 1.75rem; font-weight: 800; letter-spacing: -0.02em; }
.gh-stat-label { font-size: 0.78rem; color: var(--text-secondary); margin-top: 0.2rem; }

/* Contribution grid */
.contribution-section { padding: 1.5rem; border-radius: var(--radius-lg); }
.contribution-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 1rem; }
.contribution-title { font-size: 0.9rem; font-weight: 600; margin: 0; }
.contribution-grid { display: flex; gap: 3px; overflow-x: auto; padding-bottom: 0.5rem; }
.contrib-week { display: flex; flex-direction: column; gap: 3px; }
.contrib-day { width: 11px; height: 11px; border-radius: 2px; }
.l0 { background: rgba(255,255,255,0.06); }
.l1 { background: rgba(99,102,241,0.25); }
.l2 { background: rgba(99,102,241,0.45); }
.l3 { background: rgba(99,102,241,0.70); }
.l4 { background: var(--accent); }
.contrib-legend { display: flex; align-items: center; gap: 4px; margin-top: 0.75rem; }
.legend-box { width: 11px; height: 11px; border-radius: 2px; }

/* Repos */
.github-repos { }
.repos-title { font-size: 1rem; font-weight: 700; margin-bottom: 1rem; }
.repos-list { display: flex; flex-direction: column; gap: 0.75rem; }
.repo-card { padding: 1rem 1.25rem; border-radius: var(--radius-md); }
.repo-header { display: flex; align-items: center; gap: 0.5rem; margin-bottom: 0.4rem; }
.repo-name { font-size: 0.875rem; font-weight: 600; color: var(--accent-light); text-decoration: none; flex: 1; }
.repo-name:hover { text-decoration: underline; }
.repo-visibility {
  font-size: 0.65rem; padding: 0.1rem 0.4rem;
  border: 1px solid var(--border); border-radius: 50px; color: var(--text-muted);
}
.repo-desc { font-size: 0.78rem; color: var(--text-secondary); line-height: 1.5; margin-bottom: 0.75rem; }
.repo-meta { display: flex; gap: 1rem; align-items: center; }
.repo-lang { display: flex; align-items: center; gap: 5px; font-size: 0.75rem; color: var(--text-secondary); }
.lang-dot { width: 10px; height: 10px; border-radius: 50%; }
.repo-stat { font-size: 0.72rem; color: var(--text-muted); display: flex; align-items: center; gap: 3px; }

@media (max-width: 1100px) { .github-layout { grid-template-columns: 1fr; } .stat-row { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 500px) { .stat-row { grid-template-columns: repeat(2, 1fr); } }
</style>
