<template>
  <section id="services" class="section-padding" style="background:var(--bg-secondary)">
    <div class="container">
      <div class="text-center mb-5 reveal">
        <span class="section-label">What I Offer</span>
        <h2 class="section-title">What I <span class="gradient-text">Can Do</span></h2>
        <div class="section-divider mx-auto"></div>
        <p class="section-subtitle mx-auto">From concept to deployment — I handle the full journey of building digital products.</p>
      </div>

      <div class="services-grid">
        <div class="service-card glass-card reveal-scale" v-for="(service, idx) in services" :key="service.title" :style="{ transitionDelay: (idx * 0.08) + 's' }">
          <div class="service-icon-wrap">
            <div class="service-icon" v-html="service.icon"></div>
          </div>
          <h3 class="service-title">{{ service.title }}</h3>
          <p class="service-desc">{{ service.description }}</p>
          <div class="service-tech">
            <span class="service-tag" v-for="tech in service.tech" :key="tech">{{ tech }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ServicesSection',
  data() {
    return {
      services: [
        {
          title: 'Web Development',
          description: 'Building performant, scalable, and modern web applications using Vue.js and Node.js with clean code standards.',
          tech: ['Vue.js', 'Node.js', 'JavaScript'],
          icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>'
        },
        {
          title: 'Responsive Website Development',
          description: 'Creating fully responsive, mobile-first websites that look great and function perfectly on any screen size or device.',
          tech: ['CSS3', 'Bootstrap', 'Mobile-First'],
          icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="5" y="2" width="14" height="20" rx="2" ry="2"/><line x1="12" y1="18" x2="12.01" y2="18"/></svg>'
        },
        {
          title: 'UI/UX Implementation',
          description: 'Transforming UI designs and wireframes into pixel-perfect, interactive web interfaces with smooth animations and excellent UX.',
          tech: ['Figma', 'CSS', 'Animations'],
          icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M8 14s1.5 2 4 2 4-2 4-2"/><line x1="9" y1="9" x2="9.01" y2="9"/><line x1="15" y1="9" x2="15.01" y2="9"/></svg>'
        },
        {
          title: 'E-commerce Development',
          description: 'Developing full-featured online stores with product management, shopping cart, order tracking, and payment integration.',
          tech: ['Vue.js', 'Supabase', 'Firebase'],
          icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"/></svg>'
        },
        {
          title: 'Database Integration',
          description: 'Designing and integrating relational and cloud databases including Supabase, Firebase, and SQL-based systems.',
          tech: ['Supabase', 'Firebase', 'SQL'],
          icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/></svg>'
        },
        {
          title: 'Admin Dashboard Development',
          description: 'Building powerful admin control panels with data visualization, user management, analytics, and role-based access control.',
          tech: ['Vue.js', 'Charts', 'REST API'],
          icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/></svg>'
        },
        {
          title: 'API Integration',
          description: 'Integrating third-party APIs and building custom RESTful APIs for seamless data exchange between front-end and back-end systems.',
          tech: ['REST API', 'Node.js', 'JSON'],
          icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 20V10"/><path d="M12 20V4"/><path d="M6 20v-6"/></svg>'
        },
        {
          title: 'Mobile App Development',
          description: 'Developing cross-platform mobile applications for iOS and Android using Flutter and Dart with native-like performance.',
          tech: ['Flutter', 'Dart', 'Firebase'],
          icon: '<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="5" y="2" width="14" height="20" rx="2" ry="2"/><line x1="12" y1="18" x2="12.01" y2="18"/></svg>'
        }
      ]
    }
  }
}
</script>

<style scoped>
.services-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 1.25rem; }
.service-card { padding: 1.75rem; }
.service-icon-wrap { margin-bottom: 1.25rem; }
.service-icon {
  width: 50px; height: 50px;
  background: rgba(99,102,241,0.08); border: 1px solid rgba(99,102,241,0.18);
  border-radius: var(--radius-md);
  display: flex; align-items: center; justify-content: center;
  color: var(--accent-light); transition: var(--transition);
}
.service-card:hover .service-icon { background: rgba(99,102,241,0.2); color: var(--text-primary); }
.service-title { font-size: 0.95rem; font-weight: 700; margin-bottom: 0.6rem; }
.service-desc { font-size: 0.82rem; color: var(--text-secondary); line-height: 1.7; margin-bottom: 1rem; }
.service-tech { display: flex; flex-wrap: wrap; gap: 0.35rem; }
.service-tag {
  padding: 0.18rem 0.55rem;
  background: rgba(6,182,212,0.07); border: 1px solid rgba(6,182,212,0.18);
  border-radius: 50px; font-size: 0.68rem; color: var(--cyan); font-family: var(--font-mono);
}

@media (max-width: 1200px) { .services-grid { grid-template-columns: repeat(3, 1fr); } }
@media (max-width: 900px)  { .services-grid { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 600px)  { .services-grid { grid-template-columns: 1fr; } }
</style>

