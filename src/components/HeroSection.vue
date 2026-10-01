<template>
  <section id="home" class="hero-section">
    <!-- Animated background -->
    <div class="hero-bg">
      <div class="glow glow-1"></div>
      <div class="glow glow-2"></div>
      <div class="glow glow-3"></div>
      <div class="grid-lines"></div>
      <canvas ref="particleCanvas" class="particle-canvas"></canvas>
    </div>

    <div class="container">
      <div class="hero-inner">
        <!-- Left: Text -->
        <div class="hero-text">
          <div class="hero-badge animate-fade-up">
            <span class="badge-dot"></span>
            <span class="mono">Available for opportunities</span>
          </div>
          <p class="hero-greeting animate-fade-up" style="animation-delay:0.1s">Hi, I'm</p>
          <h1 class="hero-name animate-fade-up" style="animation-delay:0.2s">
            Hean Det<span class="cursor-blink">_</span>
          </h1>
          <h2 class="hero-title animate-fade-up" style="animation-delay:0.3s">
            <span class="gradient-text">Web Developer</span>
            <span class="divider-text"> & </span>
            <span class="gradient-text">Software Developer</span>
          </h2>
          <p class="hero-desc animate-fade-up" style="animation-delay:0.4s">
            I build modern, responsive, and user-focused web applications
            with clean design and reliable technology.
          </p>
          <div class="hero-cta animate-fade-up" style="animation-delay:0.5s">
            <a href="#projects" class="btn-primary-custom" @click.prevent="scrollTo('projects')">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/></svg>
              View My Work
            </a>
            <a href="#contact" class="btn-ghost-custom" @click.prevent="scrollTo('contact')">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
              Contact Me
            </a>
          </div>
          <!-- Tech stack pills -->
          <div class="hero-stack animate-fade-up" style="animation-delay:0.6s">
            <span class="stack-pill" v-for="tech in techStack" :key="tech">{{ tech }}</span>
          </div>
        </div>

        <!-- Right: Visual -->
        <div class="hero-visual animate-fade-up" style="animation-delay:0.3s">
          <div class="avatar-ring">
            <div class="avatar-inner">
              <img src="../assets/heandet.jpg" alt="Hean Det" class="avatar-photo" />
            </div>
          </div>
          <!-- Floating code snippets -->
          <div class="code-float code-float-1">
            <span class="mono text-accent">const</span>
            <span class="mono" style="color:#e2e8f0"> dev </span>
            <span class="mono" style="color:#94a3b8">= {</span>
          </div>
          <div class="code-float code-float-2">
            <span class="mono" style="color:#06b6d4">passion</span>
            <span class="mono" style="color:#94a3b8">: </span>
            <span class="mono" style="color:#a3e635">"code"</span>
          </div>
          <div class="code-float code-float-3">
            <span class="mono" style="color:#a855f7">status</span>
            <span class="mono" style="color:#94a3b8">: </span>
            <span class="mono" style="color:#a3e635">"building"</span>
          </div>
          <!-- Orbiting icons -->
          <div class="orbit orbit-1">
            <div class="orbit-icon">
              <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg" alt="Vue" width="28" height="28"/>
            </div>
          </div>
          <div class="orbit orbit-2">
            <div class="orbit-icon">
              <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flutter/flutter-original.svg" alt="Flutter" width="28" height="28"/>
            </div>
          </div>
          <div class="orbit orbit-3">
            <div class="orbit-icon">
              <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" alt="Node.js" width="28" height="28"/>
            </div>
          </div>
        </div>
      </div>

      <!-- Scroll indicator -->
      <div class="scroll-indicator animate-fade" style="animation-delay:1s">
        <div class="scroll-mouse">
          <div class="scroll-wheel"></div>
        </div>
        <span class="mono" style="font-size:0.7rem;color:var(--text-muted)">scroll</span>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  data() {
    return {
      techStack: ['Vue.js', 'Node.js', 'Flutter', 'JavaScript', 'Supabase', 'Firebase']
    }
  },
  mounted() {
    this.initParticles()
  },
  methods: {
    scrollTo(id) {
      document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
    },
    initParticles() {
      const canvas = this.$refs.particleCanvas
      if (!canvas) return
      const ctx = canvas.getContext('2d')
      let W = canvas.width  = canvas.offsetWidth
      let H = canvas.height = canvas.offsetHeight
      const particles = Array.from({ length: 60 }, () => ({
        x: Math.random() * W, y: Math.random() * H,
        r: Math.random() * 1.5 + 0.3,
        vx: (Math.random() - 0.5) * 0.3,
        vy: (Math.random() - 0.5) * 0.3,
        a: Math.random() * 0.5 + 0.1
      }))
      const draw = () => {
        ctx.clearRect(0, 0, W, H)
        particles.forEach(p => {
          ctx.beginPath()
          ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2)
          ctx.fillStyle = `rgba(129,140,248,${p.a})`
          ctx.fill()
          p.x += p.vx; p.y += p.vy
          if (p.x < 0 || p.x > W) p.vx *= -1
          if (p.y < 0 || p.y > H) p.vy *= -1
        })
        // connections
        for (let i = 0; i < particles.length; i++) {
          for (let j = i + 1; j < particles.length; j++) {
            const dx = particles[i].x - particles[j].x
            const dy = particles[i].y - particles[j].y
            const d = Math.sqrt(dx * dx + dy * dy)
            if (d < 100) {
              ctx.beginPath()
              ctx.moveTo(particles[i].x, particles[i].y)
              ctx.lineTo(particles[j].x, particles[j].y)
              ctx.strokeStyle = `rgba(99,102,241,${0.15 * (1 - d / 100)})`
              ctx.lineWidth = 0.5
              ctx.stroke()
            }
          }
        }
        requestAnimationFrame(draw)
      }
      draw()
      window.addEventListener('resize', () => {
        W = canvas.width  = canvas.offsetWidth
        H = canvas.height = canvas.offsetHeight
      })
    }
  }
}
</script>

<style scoped>
.hero-section {
  min-height: 100vh;
  display: flex; align-items: center;
  position: relative; overflow: hidden;
  padding: 6rem 0 4rem;
}
.hero-bg { position: absolute; inset: 0; pointer-events: none; }
.glow {
  position: absolute; border-radius: 50%;
  filter: blur(100px); opacity: 0.35;
}
.glow-1 { width: 500px; height: 500px; top: -10%; left: -5%; background: radial-gradient(circle, #4f46e5 0%, transparent 70%); }
.glow-2 { width: 400px; height: 400px; top: 30%; right: -5%; background: radial-gradient(circle, #06b6d4 0%, transparent 70%); opacity: 0.2; }
.glow-3 { width: 300px; height: 300px; bottom: 0; left: 40%; background: radial-gradient(circle, #a855f7 0%, transparent 70%); opacity: 0.15; }
.grid-lines {
  position: absolute; inset: 0;
  background-image: linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px),
                    linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
  background-size: 60px 60px;
}
.particle-canvas { position: absolute; inset: 0; width: 100%; height: 100%; }

.hero-inner {
  display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: center;
  position: relative; z-index: 1;
}
.hero-badge {
  display: inline-flex; align-items: center; gap: 0.5rem;
  padding: 0.4rem 1rem;
  background: rgba(99,102,241,0.1); border: 1px solid rgba(99,102,241,0.2);
  border-radius: 50px;
  font-size: 0.8rem; color: var(--accent-light);
  margin-bottom: 1.5rem;
}
.badge-dot {
  width: 7px; height: 7px; border-radius: 50%;
  background: #22c55e;
  box-shadow: 0 0 0 3px rgba(34,197,94,0.3);
  animation: pulse-glow 2s ease-in-out infinite;
}
.hero-greeting { font-size: 1.1rem; color: var(--text-secondary); margin-bottom: 0.25rem; }
.hero-name {
  font-size: clamp(3rem, 7vw, 5.5rem);
  font-weight: 900; letter-spacing: -0.03em; line-height: 1.05;
  color: var(--text-primary); margin-bottom: 0.5rem;
}
.cursor-blink { animation: blink 1.2s step-end infinite; color: var(--accent-light); }
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }
.hero-title { font-size: clamp(1.2rem, 2.5vw, 1.6rem); font-weight: 600; margin-bottom: 1.5rem; line-height: 1.4; }
.divider-text { color: var(--text-muted); }
.hero-desc {
  font-size: 1.05rem; color: var(--text-secondary); line-height: 1.8;
  max-width: 500px; margin-bottom: 2rem;
}
.hero-cta { display: flex; gap: 1rem; flex-wrap: wrap; margin-bottom: 2.5rem; }
.hero-stack { display: flex; gap: 0.5rem; flex-wrap: wrap; }
.stack-pill {
  padding: 0.3rem 0.85rem;
  background: rgba(255,255,255,0.04); border: 1px solid var(--border);
  border-radius: 50px;
  font-family: var(--font-mono); font-size: 0.75rem; color: var(--text-secondary);
  transition: var(--transition);
}
.stack-pill:hover { border-color: var(--border-accent); color: var(--accent-light); }

/* Visual */
.hero-visual { position: relative; display: flex; justify-content: center; align-items: center; height: 460px; }
.avatar-ring {
  width: 260px; height: 260px; border-radius: 50%;
  background: conic-gradient(from 0deg, var(--accent) 0%, var(--cyan) 33%, var(--purple) 66%, var(--accent) 100%);
  padding: 3px;
  animation: spin-slow 8s linear infinite;
}
.avatar-inner {
  width: 100%; height: 100%; border-radius: 50%;
  background: var(--bg-secondary); overflow: hidden;
  display: flex; align-items: center; justify-content: center;
}
.avatar-placeholder { text-align: center; }
.avatar-photo { width: 100%; height: 100%; object-fit: cover; object-position: center top; border-radius: 50%; }
.avatar-icon { color: var(--text-muted); margin-bottom: 0.5rem; }
.avatar-hint { font-size: 0.7rem; color: var(--text-muted); margin: 0; }

/* Floating code */
.code-float {
  position: absolute;
  background: rgba(15,15,26,0.9); border: 1px solid var(--border);
  border-radius: var(--radius-sm); padding: 0.5rem 0.75rem;
  font-size: 0.78rem; white-space: nowrap;
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 32px rgba(0,0,0,0.3);
}
.code-float-1 { top: 15%; left: -5%; animation: float 3.5s ease-in-out infinite; }
.code-float-2 { top: 45%; right: -8%; animation: float 4s ease-in-out infinite 0.5s; }
.code-float-3 { bottom: 18%; left: 0%; animation: float 3.8s ease-in-out infinite 1s; }

/* Orbiting icons */
.orbit {
  position: absolute;
  animation: orbit-rotate 6s linear infinite;
  transform-origin: 130px 130px;
}
.orbit-1 { animation-duration: 5s; top: 50%; left: 50%; margin: -130px; }
.orbit-2 { animation-duration: 7s; animation-direction: reverse; top: 50%; left: 50%; margin: -130px; }
.orbit-3 { animation-duration: 9s; top: 50%; left: 50%; margin: -130px; }
.orbit-icon {
  width: 40px; height: 40px;
  background: var(--bg-secondary); border: 1px solid var(--border);
  border-radius: 50%; display: flex; align-items: center; justify-content: center;
  box-shadow: 0 4px 16px rgba(0,0,0,0.4);
}
.orbit-1 .orbit-icon { transform: translate(110px, 10px); }
.orbit-2 .orbit-icon { transform: translate(200px, 100px); }
.orbit-3 .orbit-icon { transform: translate(20px, 200px); }
@keyframes orbit-rotate { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }

/* Scroll indicator */
.scroll-indicator {
  position: absolute; bottom: 2rem; left: 50%; transform: translateX(-50%);
  display: flex; flex-direction: column; align-items: center; gap: 0.5rem;
  z-index: 1;
}
.scroll-mouse {
  width: 24px; height: 38px; border: 2px solid var(--border);
  border-radius: 12px; display: flex; justify-content: center; padding-top: 5px;
}
.scroll-wheel {
  width: 4px; height: 8px; background: var(--accent-light);
  border-radius: 2px;
  animation: scroll-anim 1.6s ease-in-out infinite;
}
@keyframes scroll-anim { 0%{opacity:1;transform:translateY(0)} 100%{opacity:0;transform:translateY(12px)} }

@media (max-width: 992px) {
  .hero-inner { grid-template-columns: 1fr; text-align: center; gap: 3rem; }
  .hero-visual { height: 340px; }
  .hero-desc { margin: 0 auto 2rem; }
  .hero-cta { justify-content: center; }
  .hero-stack { justify-content: center; }
  .hero-badge { margin: 0 auto 1.5rem; }
  .code-float { display: none; }
  .orbit { display: none; }
  .scroll-indicator { display: none; }
}
</style>


