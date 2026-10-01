<template>
  <div id="app-wrapper">
    <NavBar />
    <main>
      <HeroSection />
      <AboutSection />
      <SkillsSection />
      <ProjectsSection />
      <ExperienceSection />
      <EducationSection />
      <ServicesSection />
      <GitHubSection />
      <ContactSection />
    </main>
    <FooterSection />
    <!-- Back to top -->
    <button class="back-to-top" :class="{ visible: showBackTop }" @click="scrollTop" aria-label="Back to top">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="18 15 12 9 6 15"/></svg>
    </button>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import EducationSection from './components/EducationSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import GitHubSection from './components/GitHubSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'

export default {
  name: 'App',
  components: {
    NavBar, HeroSection, AboutSection, SkillsSection, ProjectsSection,
    ExperienceSection, EducationSection, ServicesSection, GitHubSection,
    ContactSection, FooterSection
  },
  data() {
    return { showBackTop: false }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
    this.initReveal()
  },
  unmounted() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      this.showBackTop = window.scrollY > 400
    },
    scrollTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' })
    },
    initReveal() {
      const observer = new IntersectionObserver(
        (entries) => entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible') }),
        { threshold: 0.12 }
      )
      document.querySelectorAll('.reveal').forEach(el => observer.observe(el))
      // re-observe after short delay for dynamic content
      setTimeout(() => {
        document.querySelectorAll('.reveal:not(.visible)').forEach(el => observer.observe(el))
      }, 500)
    }
  }
}
</script>

<style>
.back-to-top {
  position: fixed; bottom: 2rem; right: 2rem; z-index: 999;
  width: 44px; height: 44px;
  background: var(--accent); color: #fff;
  border: none; border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  cursor: pointer; opacity: 0; transform: translateY(10px);
  transition: var(--transition); box-shadow: 0 4px 20px rgba(99,102,241,0.4);
}
.back-to-top.visible { opacity: 1; transform: translateY(0); }
.back-to-top:hover { background: var(--accent-dark); transform: translateY(-2px); }
</style>
