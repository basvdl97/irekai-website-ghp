<template>
  <header class="navbar" :class="{ scrolled: isScrolled }">
    <div class="container navbar-inner">

      <!-- Logo -->
      <RouterLink to="/" class="nav-logo" @click="closeMenu">
        <svg class="logo-svg" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="28" y="28" width="144" height="144" fill="none" stroke="#7aad97" stroke-width="1.6"/>
          <g stroke="#7aad97" stroke-width="1.1" stroke-opacity=".65" stroke-linecap="square">
            <line x1="17" y1="28" x2="28" y2="28"/><line x1="28" y1="17" x2="28" y2="28"/>
            <line x1="172" y1="28" x2="183" y2="28"/><line x1="172" y1="17" x2="172" y2="28"/>
            <line x1="172" y1="172" x2="183" y2="172"/><line x1="172" y1="172" x2="172" y2="183"/>
            <line x1="17" y1="172" x2="28" y2="172"/><line x1="28" y1="172" x2="28" y2="183"/>
          </g>
          <rect x="68" y="68" width="64" height="64" fill="none" stroke="#7aad97" stroke-width=".9" stroke-opacity=".42"/>
          <g stroke="#7aad97" stroke-opacity=".22" stroke-width=".7">
            <line x1="100" y1="68" x2="100" y2="132"/>
            <line x1="68" y1="100" x2="132" y2="100"/>
          </g>
          <circle cx="100" cy="100" r="6.5" fill="none" stroke="#7aad97" stroke-width="1.1" stroke-opacity=".74"/>
          <circle cx="100" cy="100" r="2.7" fill="#7aad97"/>
        </svg>
        <span class="logo-name">IREKAI</span>
      </RouterLink>

      <!-- Desktop nav -->
      <nav class="nav-links desktop-nav" aria-label="Main navigation">
        <div class="nav-item products-dropdown" ref="dropdownRef">
          <button class="nav-link dropdown-trigger" :class="{ active: isProductsRoute }" @click.stop="productsOpen = !productsOpen">
            Products
            <svg class="chevron" :class="{ open: productsOpen }" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M4 6l4 4 4-4"/>
            </svg>
          </button>
          <Transition name="dropdown">
            <div v-if="productsOpen" class="dropdown-menu">
              <RouterLink
                v-for="p in products"
                :key="p.to"
                :to="p.to"
                class="dropdown-item"
                :style="`--accent: ${p.color}`"
                @click="productsOpen = false"
              >
                <span class="dropdown-dot"></span>
                <span>{{ p.label }}</span>
              </RouterLink>
            </div>
          </Transition>
        </div>
        <RouterLink to="/about" class="nav-link" active-class="nav-link-active">About</RouterLink>
        <a href="mailto:info@irekai.nl" class="btn btn-sage nav-cta">Contact</a>
      </nav>

      <!-- Mobile burger -->
      <button class="burger" :class="{ open: menuOpen }" @click="menuOpen = !menuOpen" aria-label="Toggle menu">
        <span></span><span></span><span></span>
      </button>
    </div>

    <!-- Mobile menu -->
    <Transition name="mobile-menu">
      <div v-if="menuOpen" class="mobile-menu">
        <div class="mobile-section-label">Products</div>
        <RouterLink
          v-for="p in products"
          :key="p.to"
          :to="p.to"
          class="mobile-link"
          :style="`--accent: ${p.color}`"
          @click="closeMenu"
        >{{ p.label }}</RouterLink>
        <hr class="mobile-divider" />
        <RouterLink to="/about" class="mobile-link" @click="closeMenu">About</RouterLink>
        <a href="mailto:info@irekai.nl" class="mobile-link mobile-link-sage" @click="closeMenu">Contact →</a>
      </div>
    </Transition>
  </header>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted, watch } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const menuOpen = ref(false)
const productsOpen = ref(false)
const isScrolled = ref(false)
const dropdownRef = ref(null)

const products = [
  { to: '/products/quantum-readiness',   label: 'Quantum Readiness Assessment',  color: '#7aad97' },
  { to: '/products/maturity-model',      label: 'PQC Maturity Model',            color: '#fbbf24' },
  { to: '/products/supplier-management', label: 'Supplier Management Programme',  color: '#a78bfa' },
  { to: '/products/code-scanning',       label: 'Cryptographic Code Scanner',    color: '#e879f9' },
]

const isProductsRoute = computed(() => route.path.startsWith('/products'))
function closeMenu() { menuOpen.value = false }
function onScroll() { isScrolled.value = window.scrollY > 24 }

function onClickOutside(e) {
  if (dropdownRef.value && !dropdownRef.value.contains(e.target)) {
    productsOpen.value = false
  }
}

// Close dropdown on route change
watch(() => route.path, () => { productsOpen.value = false; menuOpen.value = false })

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })
  document.addEventListener('click', onClickOutside)
})
onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
  document.removeEventListener('click', onClickOutside)
})
</script>

<style scoped>
.navbar {
  position: sticky; top: 0; z-index: 100;
  border-bottom: 1px solid transparent;
  transition: border-color .2s, background .2s, backdrop-filter .2s;
}
.navbar.scrolled {
  background: rgba(12,10,9,.85);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom-color: var(--border);
}
.navbar-inner { display: flex; align-items: center; justify-content: space-between; height: 60px; }

.nav-logo { display: flex; align-items: center; gap: .6rem; text-decoration: none; }
.logo-svg  { width: 28px; height: 28px; }
.logo-name { font-family: var(--font-display); font-size: 1rem; letter-spacing: .18em; color: var(--text); }

.desktop-nav { display: none; }
@media (min-width: 768px) { .desktop-nav { display: flex; align-items: center; gap: .25rem; } }

.nav-links { display: flex; align-items: center; gap: .25rem; }
.nav-link {
  font-family: var(--font-mono); font-size: .72rem; letter-spacing: .05em;
  color: var(--text-muted); padding: .4rem .75rem; border-radius: 6px;
  background: transparent; border: none; cursor: pointer;
  display: flex; align-items: center; gap: .3rem;
  transition: color .15s, background .15s; text-decoration: none;
}
.nav-link:hover, .nav-link-active, .nav-link.active {
  color: var(--text); background: rgba(255,255,255,.05);
}
.nav-cta { margin-left: .5rem; }

.btn-sage {
  display: inline-flex; align-items: center; gap: .5rem;
  font-family: var(--font-mono); font-size: .72rem; padding: .38rem .9rem;
  border-radius: 6px; border: 1px solid rgba(122,173,151,.4);
  background: rgba(122,173,151,.1); color: #7aad97;
  transition: all .2s; text-decoration: none;
}
.btn-sage:hover {
  background: rgba(122,173,151,.18); border-color: rgba(122,173,151,.7);
  box-shadow: 0 0 18px -5px rgba(122,173,151,.4);
}

.products-dropdown { position: relative; }
.chevron { width: 10px; height: 10px; transition: transform .2s; }
.chevron.open { transform: rotate(180deg); }

.dropdown-menu {
  position: absolute; top: calc(100% + 8px); left: 50%; transform: translateX(-50%);
  min-width: 265px; background: #1a1714;
  border: 1px solid var(--border); border-radius: 10px;
  padding: .4rem; box-shadow: 0 16px 48px rgba(0,0,0,.5);
}
.dropdown-item {
  display: flex; align-items: center; gap: .6rem;
  padding: .55rem .75rem; border-radius: 6px;
  font-family: var(--font-mono); font-size: .7rem;
  color: var(--text-muted); text-decoration: none;
  transition: background .15s, color .15s;
}
.dropdown-item:hover { background: rgba(255,255,255,.06); color: var(--text); }
.dropdown-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--accent, #7aad97); flex-shrink: 0; }

.dropdown-enter-active, .dropdown-leave-active { transition: opacity .15s, transform .15s; }
.dropdown-enter-from, .dropdown-leave-to { opacity: 0; transform: translateX(-50%) translateY(-4px); }

.burger {
  display: flex; flex-direction: column; justify-content: space-between;
  width: 22px; height: 14px; background: transparent; border: none; cursor: pointer; padding: 0;
}
@media (min-width: 768px) { .burger { display: none; } }
.burger span {
  display: block; height: 1.5px; background: var(--text-muted);
  border-radius: 2px; transition: all .25s ease; transform-origin: center;
}
.burger.open span:nth-child(1) { transform: translateY(6.25px) rotate(45deg); }
.burger.open span:nth-child(2) { opacity: 0; transform: scaleX(0); }
.burger.open span:nth-child(3) { transform: translateY(-6.25px) rotate(-45deg); }

.mobile-menu {
  display: flex; flex-direction: column;
  padding: .75rem 1.5rem 1.5rem;
  border-bottom: 1px solid var(--border);
  background: rgba(12,10,9,.97); backdrop-filter: blur(12px);
}
@media (min-width: 768px) { .mobile-menu { display: none; } }
.mobile-section-label {
  font-family: var(--font-mono); font-size: .6rem; letter-spacing: .2em;
  text-transform: uppercase; color: var(--text-dim); margin-bottom: .5rem; margin-top: .25rem;
}
.mobile-link {
  font-family: var(--font-mono); font-size: .8rem; color: var(--text-muted);
  padding: .6rem .5rem; border-radius: 6px; text-decoration: none;
  transition: color .15s, background .15s; display: flex; align-items: center; gap: .5rem;
}
.mobile-link::before { content: ''; width: 5px; height: 5px; border-radius: 50%; background: var(--accent, var(--border)); flex-shrink: 0; }
.mobile-link:hover { color: var(--text); background: rgba(255,255,255,.04); }
.mobile-link-sage { color: #7aad97; }
.mobile-divider { border: none; border-top: 1px solid var(--border); margin: .5rem 0; }

.mobile-menu-enter-active, .mobile-menu-leave-active { transition: opacity .2s, transform .2s; }
.mobile-menu-enter-from, .mobile-menu-leave-to { opacity: 0; transform: translateY(-8px); }
</style>
