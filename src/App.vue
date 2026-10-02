<template>
  <div id="app-wrapper">
    <!-- Fire trail canvas -->
    <canvas ref="fireCanvas" class="fire-canvas"></canvas>
    <!-- Custom cursor dot -->
    <div class="cursor-dot" ref="cursorDot"></div>

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
    return {
      showBackTop: false,
      mouseX: -200,
      mouseY: -200,
      particles: [],
      animFrame: null,
      isTouch: false
    }
  },
  mounted() {
    // Detect touch device - skip fire on touch
    this.isTouch = window.matchMedia('(hover: none) and (pointer: coarse)').matches
    window.addEventListener('scroll', this.handleScroll)
    if (!this.isTouch) {
      window.addEventListener('mousemove', this.handleMouseMove)
      document.addEventListener('mouseleave', this.hideCursor)
      document.addEventListener('mouseenter', this.showCursor)
      this.initFireCanvas()
      this.fireLoop()
    }
    this.initReveal()
    this.initTilt()
    this.initRipple()
  },
  unmounted() {
    window.removeEventListener('scroll', this.handleScroll)
    window.removeEventListener('mousemove', this.handleMouseMove)
    if (this.animFrame) cancelAnimationFrame(this.animFrame)
  },
  methods: {
    handleScroll() {
      this.showBackTop = window.scrollY > 400
    },
    scrollTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' })
    },
    handleMouseMove(e) {
      this.mouseX = e.clientX
      this.mouseY = e.clientY

      // Move cursor dot instantly
      const dot = this.$refs.cursorDot
      if (dot) {
        dot.style.left = e.clientX + 'px'
        dot.style.top  = e.clientY + 'px'
      }

      // Spawn fire particles on move
      for (let i = 0; i < 4; i++) {
        this.spawnParticle(e.clientX, e.clientY)
      }
    },
    hideCursor() {
      if (this.$refs.cursorDot) this.$refs.cursorDot.style.opacity = '0'
    },
    showCursor() {
      if (this.$refs.cursorDot) this.$refs.cursorDot.style.opacity = '1'
    },
    initFireCanvas() {
      const canvas = this.$refs.fireCanvas
      if (!canvas) return
      canvas.width  = window.innerWidth
      canvas.height = window.innerHeight
      window.addEventListener('resize', () => {
        canvas.width  = window.innerWidth
        canvas.height = window.innerHeight
      })
    },
    spawnParticle(x, y) {
      // Random fire colors: yellow -> orange -> red -> dark red
      const colors = [
        [255, 255, 80],   // bright yellow
        [255, 180, 20],   // orange-yellow
        [255, 100, 10],   // orange
        [255, 50,  0],    // red-orange
        [200, 20,  0],    // red
      ]
      const c = colors[Math.floor(Math.random() * colors.length)]
      this.particles.push({
        x: x + (Math.random() - 0.5) * 12,
        y: y + (Math.random() - 0.5) * 6,
        vx: (Math.random() - 0.5) * 1.2,
        vy: -(Math.random() * 2.5 + 1.5),  // rise upward
        size: Math.random() * 10 + 4,
        alpha: 1,
        decay: Math.random() * 0.025 + 0.018,
        r: c[0], g: c[1], b: c[2]
      })
    },
    fireLoop() {
      const canvas = this.$refs.fireCanvas
      if (!canvas) return
      const ctx = canvas.getContext('2d')

      ctx.clearRect(0, 0, canvas.width, canvas.height)

      this.particles = this.particles.filter(p => p.alpha > 0.01)

      for (const p of this.particles) {
        // Flicker: add slight wobble
        p.x  += p.vx + Math.sin(Date.now() * 0.01 + p.y) * 0.3
        p.y  += p.vy
        p.vy *= 0.98          // slow vertical rise slightly
        p.size *= 0.97        // shrink as it rises
        p.alpha -= p.decay

        // Draw flame particle as radial gradient blob
        const grad = ctx.createRadialGradient(p.x, p.y, 0, p.x, p.y, p.size)
        grad.addColorStop(0,   `rgba(${p.r},${p.g},${p.b},${p.alpha})`)
        grad.addColorStop(0.4, `rgba(${p.r},${Math.max(0,p.g-60)},0,${p.alpha * 0.7})`)
        grad.addColorStop(1,   `rgba(${Math.max(0,p.r-80)},0,0,0)`)

        ctx.beginPath()
        ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2)
        ctx.fillStyle = grad
        ctx.fill()
      }

      this.animFrame = requestAnimationFrame(this.fireLoop)
    },
    initReveal() {
      const observer = new IntersectionObserver(
        (entries) => entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible') }),
        { threshold: 0.1 }
      )
      const selectors = '.reveal, .reveal-left, .reveal-right, .reveal-scale'
      document.querySelectorAll(selectors).forEach(el => observer.observe(el))
      setTimeout(() => {
        document.querySelectorAll(`${selectors}:not(.visible)`).forEach(el => observer.observe(el))
      }, 500)
    },
    initTilt() {
      setTimeout(() => {
        document.querySelectorAll('.glass-card').forEach(card => {
          card.classList.add('tilt-card')
          card.addEventListener('mousemove', (e) => {
            const r = card.getBoundingClientRect()
            const x = (e.clientX - r.left) / r.width  - 0.5
            const y = (e.clientY - r.top)  / r.height - 0.5
            card.style.transform = `perspective(600px) rotateY(${x * 8}deg) rotateX(${-y * 8}deg) translateY(-4px)`
          })
          card.addEventListener('mouseleave', () => { card.style.transform = '' })
        })
      }, 800)
    },
    initRipple() {
      setTimeout(() => {
        document.querySelectorAll('.btn-primary-custom, .btn-ghost-custom').forEach(btn => {
          btn.addEventListener('click', (e) => {
            const ripple = document.createElement('span')
            ripple.className = 'ripple'
            const r = btn.getBoundingClientRect()
            const size = Math.max(r.width, r.height)
            ripple.style.cssText = `width:${size}px;height:${size}px;left:${e.clientX - r.left - size/2}px;top:${e.clientY - r.top - size/2}px`
            btn.appendChild(ripple)
            setTimeout(() => ripple.remove(), 700)
          })
        })
      }, 800)
    }
  }
}
</script>

<style>
/* ---- Fire canvas ---- */
.fire-canvas {
  position: fixed;
  top: 0; left: 0;
  width: 100vw; height: 100vh;
  pointer-events: none;
  z-index: 99998;
}

/* ---- Cursor dot (flame tip) ---- */
.cursor-dot {
  position: fixed;
  width: 10px; height: 10px;
  border-radius: 50%;
  pointer-events: none;
  z-index: 99999;
  transform: translate(-50%, -50%);
  background: radial-gradient(circle, #fff9c4 0%, #ffeb3b 40%, #ff6f00 100%);
  box-shadow:
    0 0 6px  rgba(255, 200, 0, 1),
    0 0 16px rgba(255, 120, 0, 0.8),
    0 0 32px rgba(255, 60,  0, 0.5);
  transition: opacity 0.3s ease;
}

/* ---- Hide on touch ---- */
@media (hover: none) and (pointer: coarse) {
  .cursor-dot, .fire-canvas { display: none; }
}

/* ---- Back to top ---- */
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
