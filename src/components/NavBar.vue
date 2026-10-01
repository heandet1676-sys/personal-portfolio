<template>
  <nav class="navbar-custom" :class="{ scrolled: isScrolled, 'menu-open': mobileOpen }">
    <div class="container">
      <div class="nav-inner">
        <!-- Logo -->
        <a href="#home" class="nav-logo" @click.prevent="scrollTo('home')">
          <span class="logo-bracket mono">&lt;</span>
          <span class="logo-name">HD</span>
          <span class="logo-bracket mono">/&gt;</span>
        </a>

        <!-- Desktop links -->
        <ul class="nav-links" role="list">
          <li v-for="link in navLinks" :key="link.id">
            <a :href="'#' + link.id" class="nav-link" :class="{ active: activeSection === link.id }"
               @click.prevent="scrollTo(link.id)">{{ link.label }}</a>
          </li>
        </ul>

        <!-- CTA + Hamburger -->
        <div class="nav-actions">
          <a href="#contact" class="btn-primary-custom btn-sm-nav" @click.prevent="scrollTo('contact')">
            Let's Talk
          </a>
          <button class="hamburger" :class="{ open: mobileOpen }" @click="toggleMobile" aria-label="Toggle menu">
            <span></span><span></span><span></span>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile menu -->
    <div class="mobile-menu" :class="{ open: mobileOpen }">
      <ul role="list">
        <li v-for="link in navLinks" :key="link.id">
          <a :href="'#' + link.id" @click.prevent="mobileNav(link.id)">{{ link.label }}</a>
        </li>
        <li>
          <a href="#contact" class="btn-primary-custom w-100 justify-content-center mt-2" @click.prevent="mobileNav('contact')">Let's Talk</a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  data() {
    return {
      isScrolled: false,
      mobileOpen: false,
      activeSection: 'home',
      navLinks: [
        { id: 'home',       label: 'Home' },
        { id: 'about',      label: 'About' },
        { id: 'skills',     label: 'Skills' },
        { id: 'projects',   label: 'Projects' },
        { id: 'experience', label: 'Experience' },
        { id: 'education',  label: 'Education' },
        { id: 'contact',    label: 'Contact' }
      ]
    }
  },
  mounted() {
    window.addEventListener('scroll', this.onScroll)
  },
  unmounted() {
    window.removeEventListener('scroll', this.onScroll)
  },
  methods: {
    onScroll() {
      this.isScrolled = window.scrollY > 40
      // active section detection
      const sections = this.navLinks.map(l => document.getElementById(l.id)).filter(Boolean)
      const scrollY = window.scrollY + 120
      for (let i = sections.length - 1; i >= 0; i--) {
        if (sections[i].offsetTop <= scrollY) {
          this.activeSection = sections[i].id; break
        }
      }
    },
    scrollTo(id) {
      const el = document.getElementById(id)
      if (el) el.scrollIntoView({ behavior: 'smooth' })
      this.mobileOpen = false
    },
    toggleMobile() { this.mobileOpen = !this.mobileOpen },
    mobileNav(id) { this.scrollTo(id); this.mobileOpen = false }
  }
}
</script>

<style scoped>
.navbar-custom {
  position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
  padding: 1.2rem 0;
  transition: background 0.4s ease, backdrop-filter 0.4s ease, box-shadow 0.4s ease, padding 0.3s ease;
}
.navbar-custom.scrolled {
  background: rgba(10,10,15,0.85);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  box-shadow: 0 1px 0 rgba(255,255,255,0.05);
  padding: 0.75rem 0;
}
.nav-inner {
  display: flex; align-items: center; justify-content: space-between; gap: 2rem;
}
.nav-logo {
  font-family: var(--font-mono); font-size: 1.25rem; font-weight: 600;
  text-decoration: none; color: var(--text-primary);
  display: flex; align-items: center; gap: 2px;
}
.logo-bracket { color: var(--accent-light); }
.logo-name { color: var(--text-primary); margin: 0 1px; }
.nav-links {
  display: flex; align-items: center; gap: 0.25rem;
  list-style: none; margin: 0; padding: 0;
}
.nav-link {
  padding: 0.4rem 0.85rem;
  font-size: 0.875rem; font-weight: 500;
  color: var(--text-secondary); text-decoration: none;
  border-radius: var(--radius-sm);
  transition: var(--transition);
}
.nav-link:hover, .nav-link.active { color: var(--text-primary); background: rgba(255,255,255,0.06); }
.nav-link.active { color: var(--accent-light); }
.nav-actions { display: flex; align-items: center; gap: 1rem; }
.btn-sm-nav { padding: 0.55rem 1.2rem; font-size: 0.875rem; }

/* Hamburger */
.hamburger { display: none; flex-direction: column; gap: 5px; background: none; border: none; cursor: pointer; padding: 4px; }
.hamburger span {
  display: block; width: 22px; height: 2px;
  background: var(--text-primary); border-radius: 2px;
  transition: var(--transition); transform-origin: center;
}
.hamburger.open span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
.hamburger.open span:nth-child(2) { opacity: 0; transform: scaleX(0); }
.hamburger.open span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }

/* Mobile menu */
.mobile-menu {
  display: none;
  position: absolute; top: 100%; left: 0; right: 0;
  background: rgba(10,10,15,0.97);
  backdrop-filter: blur(24px);
  border-top: 1px solid var(--border);
  padding: 1.5rem;
  transform: translateY(-10px); opacity: 0;
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.mobile-menu ul { list-style: none; margin: 0; padding: 0; display: flex; flex-direction: column; gap: 0.5rem; }
.mobile-menu a {
  display: block; padding: 0.75rem 1rem;
  color: var(--text-secondary); text-decoration: none; font-weight: 500;
  border-radius: var(--radius-sm); transition: var(--transition);
}
.mobile-menu a:hover { color: var(--text-primary); background: rgba(255,255,255,0.05); }
.mobile-menu.open { transform: translateY(0); opacity: 1; }

@media (max-width: 768px) {
  .nav-links, .btn-sm-nav { display: none; }
  .hamburger { display: flex; }
  .mobile-menu { display: block; }
}
</style>
