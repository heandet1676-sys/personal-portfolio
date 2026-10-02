<template>
  <section id="education" class="section-padding">
    <div class="container">
      <div class="text-center mb-5 reveal">
        <span class="section-label">Academic Background</span>
        <h2 class="section-title">Education & <span class="gradient-text">Learning</span></h2>
        <div class="section-divider mx-auto"></div>
      </div>

      <div class="edu-grid">
        <div class="edu-card glass-card reveal-right" v-for="(edu, idx) in education" :key="idx" :style="{ transitionDelay: (idx * 0.1) + 's' }">
          <div class="edu-icon-wrap">
            <div class="edu-icon" v-html="edu.icon"></div>
          </div>
          <div class="edu-body">
            <div class="edu-period mono">{{ edu.period }}</div>
            <h3 class="edu-degree">{{ edu.degree }}</h3>
            <p class="edu-institution">{{ edu.institution }}</p>
            <p class="edu-description">{{ edu.description }}</p>
            <div class="edu-subjects" v-if="edu.subjects">
              <p class="subjects-label">Key subjects</p>
              <div class="subjects-list">
                <span class="subject-tag" v-for="subject in edu.subjects" :key="subject">{{ subject }}</span>
              </div>
            </div>
            <div class="edu-achievements" v-if="edu.achievements">
              <div class="achievement-item" v-for="ach in edu.achievements" :key="ach">
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="color:var(--accent-light);flex-shrink:0"><polyline points="20 6 9 17 4 12"/></svg>
                <span>{{ ach }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Certifications -->
      <div class="cert-section reveal mt-5">
        <h3 class="cert-title">Certifications & Online Courses</h3>
        <div class="cert-grid">
          <div class="cert-card glass-card" v-for="cert in certifications" :key="cert.name">
            <div class="cert-icon" v-html="cert.icon"></div>
            <div class="cert-info">
              <p class="cert-name">{{ cert.name }}</p>
              <p class="cert-provider mono">{{ cert.provider }}</p>
            </div>
            <div class="cert-year mono">{{ cert.year }}</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'EducationSection',
  data() {
    return {
      education: [
        {
          degree: 'Bachelor of Science in Information Technology',
          institution: 'University — Cambodia',
          period: '2022 – Present',
          description: 'Pursuing a degree in Information Technology with a strong focus on software engineering, web development, and database systems.',
          subjects: ['Data Structures', 'Algorithms', 'Database Systems', 'Web Development', 'Software Engineering', 'UI/UX Design', 'Computer Networks'],
          achievements: ['Active member of the campus development club', 'Built multiple academic projects', 'Self-learning advanced web frameworks alongside coursework'],
          icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 10v6M2 10l10-5 10 5-10 5z"/><path d="M6 12v5c3 3 9 3 12 0v-5"/></svg>'
        },
        {
          degree: 'High School Diploma',
          institution: 'High School — Cambodia',
          period: '2019 – 2022',
          description: 'Completed high school education with an interest in mathematics and science, which built the analytical foundation for programming.',
          subjects: ['Mathematics', 'Physics', 'Computer Basics', 'Sciences'],
          achievements: [],
          icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"/><line x1="3" y1="9" x2="21" y2="9"/><line x1="9" y1="21" x2="9" y2="9"/></svg>'
        }
      ],
      certifications: [
        {
          name: 'Vue.js Advanced Development',
          provider: 'Online Learning',
          year: '2024',
          icon: '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="8" r="6"/><path d="M15.477 12.89L17 22l-5-3-5 3 1.523-9.11"/></svg>'
        },
        {
          name: 'Flutter & Dart Mobile Development',
          provider: 'Self-Study',
          year: '2023',
          icon: '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="8" r="6"/><path d="M15.477 12.89L17 22l-5-3-5 3 1.523-9.11"/></svg>'
        },
        {
          name: 'JavaScript Fundamentals',
          provider: 'Online Courses',
          year: '2023',
          icon: '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="8" r="6"/><path d="M15.477 12.89L17 22l-5-3-5 3 1.523-9.11"/></svg>'
        },
        {
          name: 'Database Design & SQL',
          provider: 'Academic Coursework',
          year: '2023',
          icon: '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="8" r="6"/><path d="M15.477 12.89L17 22l-5-3-5 3 1.523-9.11"/></svg>'
        }
      ]
    }
  }
}
</script>

<style scoped>
.edu-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem; }
.edu-card { padding: 2rem; display: flex; gap: 1.25rem; }
.edu-icon-wrap { flex-shrink: 0; }
.edu-icon {
  width: 48px; height: 48px;
  background: rgba(99,102,241,0.1); border: 1px solid rgba(99,102,241,0.2);
  border-radius: var(--radius-sm);
  display: flex; align-items: center; justify-content: center;
  color: var(--accent-light);
}
.edu-period { font-size: 0.75rem; color: var(--accent-light); margin-bottom: 0.4rem; }
.edu-degree { font-size: 1rem; font-weight: 700; margin-bottom: 0.25rem; }
.edu-institution { font-size: 0.875rem; color: var(--text-secondary); margin-bottom: 0.75rem; }
.edu-description { font-size: 0.85rem; color: var(--text-secondary); line-height: 1.7; margin-bottom: 1rem; }
.subjects-label { font-size: 0.78rem; color: var(--text-muted); margin-bottom: 0.5rem; font-weight: 500; }
.subjects-list { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-bottom: 1rem; }
.subject-tag {
  padding: 0.2rem 0.6rem;
  background: rgba(255,255,255,0.04); border: 1px solid var(--border);
  border-radius: 50px; font-size: 0.72rem; color: var(--text-muted); font-family: var(--font-mono);
}
.achievement-item { display: flex; align-items: flex-start; gap: 0.5rem; font-size: 0.82rem; color: var(--text-secondary); margin-bottom: 0.35rem; }

/* Certifications */
.cert-title { font-size: 1.1rem; font-weight: 700; margin-bottom: 1.25rem; }
.cert-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1rem; }
.cert-card {
  padding: 1rem 1.25rem;
  display: flex; align-items: center; gap: 1rem;
  border-radius: var(--radius-md);
}
.cert-icon {
  width: 36px; height: 36px; flex-shrink: 0;
  background: rgba(99,102,241,0.1); border-radius: var(--radius-sm);
  display: flex; align-items: center; justify-content: center; color: var(--accent-light);
}
.cert-name { font-size: 0.875rem; font-weight: 600; margin: 0; }
.cert-provider { font-size: 0.72rem; color: var(--text-muted); margin: 0; }
.cert-year { font-size: 0.72rem; color: var(--text-muted); margin-left: auto; }

@media (max-width: 900px) { .edu-grid { grid-template-columns: 1fr; } .cert-grid { grid-template-columns: 1fr; } }
@media (max-width: 600px) { .edu-card { flex-direction: column; } }
</style>

