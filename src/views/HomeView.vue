<template>
  <div>
    <!-- ─── HERO: IREMIA + IKIGAI → IREKAI (loops) ──────────────────── -->
    <section class="hero-section">
      <div class="hero-center">

        <!-- Seal mark -->
        <div class="seal-area" ref="sealEl">
          <svg width="148" height="148" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
            <defs>
              <pattern id="h-lat" x="0" y="0" width="12" height="12"
                patternUnits="userSpaceOnUse" patternTransform="rotate(45 100 100)">
                <circle cx="0" cy="0" r="1.3" fill="#7aad97" fill-opacity=".55"/>
              </pattern>
              <clipPath id="h-clip">
                <rect x="69" y="69" width="62" height="62"/>
              </clipPath>
            </defs>
            <rect class="seal-rect-outer"
              x="28" y="28" width="144" height="144"
              fill="none" stroke="#7aad97" stroke-width="1.6"/>
            <g class="seal-corners"
               stroke="#7aad97" stroke-width="1.1" stroke-opacity=".65" stroke-linecap="square">
              <line x1="17" y1="28" x2="28" y2="28"/><line x1="28" y1="17" x2="28" y2="28"/>
              <line x1="172" y1="28" x2="183" y2="28"/><line x1="172" y1="17" x2="172" y2="28"/>
              <line x1="172" y1="172" x2="183" y2="172"/><line x1="172" y1="172" x2="172" y2="183"/>
              <line x1="17" y1="172" x2="28" y2="172"/><line x1="28" y1="172" x2="28" y2="183"/>
            </g>
            <g class="seal-lattice">
              <rect x="69" y="69" width="62" height="62" fill="url(#h-lat)" clip-path="url(#h-clip)"/>
            </g>
            <rect class="seal-rect-inner"
              x="68" y="68" width="64" height="64"
              fill="none" stroke="#7aad97" stroke-width=".9" stroke-opacity=".42"/>
            <g class="seal-axes" stroke="#7aad97" stroke-opacity=".22" stroke-width=".7">
              <line x1="100" y1="68" x2="100" y2="132"/>
              <line x1="68" y1="100" x2="132" y2="100"/>
            </g>
            <circle class="seal-ring"
              cx="100" cy="100" r="6.5"
              fill="none" stroke="#7aad97" stroke-width="1.1" stroke-opacity=".74"/>
            <circle class="seal-dot" cx="100" cy="100" r="2.7" fill="#7aad97"/>
          </svg>
        </div>

        <!-- Name row: IREMIA | IKIGAI → IREKAI -->
        <div class="name-area" aria-label="IREKAI">
          <!-- IREMIA: I R E keep; M I A fade -->
          <span class="lw keep" ref="lw0"><span class="lt">I</span></span>
          <span class="lw keep" ref="lw1"><span class="lt">R</span></span>
          <span class="lw keep" ref="lw2"><span class="lt">E</span></span>
          <span class="lw fade"  ref="lw3"><span class="lt">M</span></span>
          <span class="lw fade"  ref="lw4"><span class="lt">I</span></span>
          <span class="lw fade"  ref="lw5"><span class="lt">A</span></span>
          <!-- Spacer -->
          <span class="lw spacer" ref="spacerEl">
            <span class="spacer-line" ref="spacerLineEl"></span>
          </span>
          <!-- IKIGAI: I fade; K keep; I G fade; A I keep -->
          <span class="lw fade"  ref="lw6"><span class="lt">I</span></span>
          <span class="lw keep"  ref="lw7"><span class="lt">K</span></span>
          <span class="lw fade"  ref="lw8"><span class="lt">I</span></span>
          <span class="lw fade"  ref="lw9"><span class="lt">G</span></span>
          <span class="lw keep"  ref="lw10"><span class="lt">A</span></span>
          <span class="lw keep"  ref="lw11"><span class="lt">I</span></span>
        </div>

        <!-- Etymology labels → tagline -->
        <div class="below-area">
          <div class="labels-row" ref="labelsEl">
            <div class="word-label">
              <span class="lbl-glyph">ἠρεμία</span>
              <span class="lbl-meaning">Greek · stillness</span>
            </div>
            <div class="word-label">
              <span class="lbl-glyph">意気概</span>
              <span class="lbl-meaning">Japanese · purpose</span>
            </div>
          </div>
          <p class="hero-tagline" ref="taglineEl">
            Cryptographic clarity first. Migrate with peace of mind.
          </p>
        </div>

      </div>

    </section>

    <!-- ─── PRODUCTS OVERVIEW ──────────────────────────────────────── -->
    <section class="products-section" id="products">
      <div class="container">
        <div class="section-head">
          <div class="section-label">Products &amp; Services</div>
          <h2 class="section-title font-display">
            Everything you need to become<br/>
            <em style="color:var(--sage)">quantum&#8209;ready</em>
          </h2>
          <p class="section-sub">
            From initial awareness to continuous cryptographic assurance — IREKAI's tools
            and frameworks guide your organisation at every step.
          </p>
        </div>

        <div class="products-grid">
          <RouterLink to="/products/quantum-readiness" class="product-card product-card--featured sage">
            <div class="card-badge sage-badge">Featured · Flagship product</div>
            <div class="card-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
              </svg>
            </div>
            <h3 class="card-title">Quick Quantum Readiness Assessment</h3>
            <p class="card-desc">
              Our flagship product. Understand your organisation's cryptographic posture in 4-6 weeks,
              not months. Pinpoint your most critical business cases, prioritise high risks, and walk away with a concrete
              cryptographic migration roadmap tailored to your core business.
            </p>
            <div class="card-tags">
              <span class="tag">Assessment</span>
              <span class="tag">Risk scoring</span>
              <span class="tag">Roadmap</span>
            </div>
            <div class="card-cta">Start assessment <span class="arrow">→</span></div>
          </RouterLink>

          <RouterLink to="/products/maturity-model" class="product-card amber">
            <div class="card-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                <path d="M2 20h20M6 20V10M12 20V4M18 20v-8"/>
              </svg>
            </div>
            <h3 class="card-title">PQC Migration Maturity Model</h3>
            <p class="card-desc">
              A five-tier maturity framework across five dimensions. Track your progress,
              identify gaps, and drive your quantum migration with structured milestones.
            </p>
            <div class="card-tags">
              <span class="tag">Framework</span>
              <span class="tag">5 dimensions</span>
              <span class="tag">Interactive</span>
            </div>
            <div class="card-cta">Explore model <span class="arrow">→</span></div>
          </RouterLink>

          <RouterLink to="/products/supplier-management" class="product-card violet">
            <div class="card-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/>
                <circle cx="9" cy="7" r="4"/>
                <path d="M23 21v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75"/>
              </svg>
            </div>
            <h3 class="card-title">Supplier Management Programme</h3>
            <p class="card-desc">
              Quantum threats are pushed up the supply chain. Systematically assess vendors,
              embed PQC requirements in contracts, and verify your entire supply chain.
            </p>
            <div class="card-tags">
              <span class="tag">Supply chain</span>
              <span class="tag">Risk assessment</span>
              <span class="tag">Contracts</span>
            </div>
            <div class="card-cta">View programme <span class="arrow">→</span></div>
          </RouterLink>

          <RouterLink to="/products/code-scanning" class="product-card fuchsia">
            <div class="card-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                <polyline points="16 18 22 12 16 6"/>
                <polyline points="8 6 2 12 8 18"/>
              </svg>
            </div>
            <h3 class="card-title">Cryptographic Code Scanner</h3>
            <p class="card-desc">
              Automated static analysis of your codebase. Detect vulnerable keys and algorithms,
              assess cryptographic agility, and gain insight in every quantum-vulnerable dependency.
            </p>
            <div class="card-tags">
              <span class="tag">SAST</span>
              <span class="tag">Crypto agility</span>
              <span class="tag">CBOM</span>
            </div>
            <div class="card-cta">Learn more <span class="arrow">→</span></div>
          </RouterLink>
        </div>
      </div>
    </section>

    <!-- ─── WHY IREKAI ─────────────────────────────────────────────── -->
    <section class="why-section">
      <div class="container">
        <div class="section-label" style="margin-bottom:1.25rem;">Why IREKAI</div>
        <div class="why-grid">
          <div class="why-item" v-for="w in whyItems" :key="w.title">
            <div class="why-icon" v-html="w.icon"></div>
            <div>
              <div class="why-title">{{ w.title }}</div>
              <div class="why-body">{{ w.body }}</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ─── CTA BANNER ─────────────────────────────────────────────── -->
    <section class="cta-section">
      <div class="container cta-inner">
        <div class="cta-text">
          <p class="section-label" style="margin-bottom:0.75rem;">Get started</p>
          <h2 class="font-display" style="font-size:clamp(1.6rem,4vw,2.5rem);line-height:1.15;color:var(--text);">
            Ready to assess your<br/><em style="color:var(--sage)">quantum exposure</em>?
          </h2>
        </div>
        <div class="cta-actions">
          <RouterLink to="/products/quantum-readiness" class="btn btn-sage" style="font-size:0.8rem;padding:0.7rem 1.5rem;">
            Start free assessment →
          </RouterLink>
          <a href="mailto:info@irekai.nl" class="btn btn-ghost" style="font-size:0.8rem;padding:0.7rem 1.5rem;">
            Talk to an expert
          </a>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// ── Template refs ────────────────────────────────────────────────────
const sealEl       = ref(null)
const spacerEl     = ref(null)
const spacerLineEl = ref(null)
const labelsEl     = ref(null)
const taglineEl    = ref(null)
const lw0 = ref(null); const lw1 = ref(null); const lw2  = ref(null)
const lw3 = ref(null); const lw4 = ref(null); const lw5  = ref(null)
const lw6 = ref(null); const lw7 = ref(null); const lw8  = ref(null)
const lw9 = ref(null); const lw10 = ref(null); const lw11 = ref(null)

const fadeIds = [3, 4, 5, 6, 8, 9]

const T = {
  p1Start:       180,
  p1Stagger:      75,
  p2Start:       880,
  p2Stagger:      75,
  labelsIn:     1680,
  dimStart:     2900,
  collapseStart:3680,
  sealIn:       4480,
  sealDraw:     4880,
  labelsFade:   3680,
  tagIn:        4700,
}

let timers = []
function after(ms, fn) { timers.push(setTimeout(fn, ms)) }

function run() {

  const lws = [lw0,lw1,lw2,lw3,lw4,lw5,lw6,lw7,lw8,lw9,lw10,lw11].map(r => r.value)

  // Phase 1: reveal IREMIA
  for (let i = 0; i < 6; i++) {
    after(T.p1Start + i * T.p1Stagger, () => { if (lws[i]) lws[i].classList.add('visible') })
  }

  // Phase 2: reveal IKIGAI + spacer line
  for (let i = 0; i < 6; i++) {
    after(T.p2Start + i * T.p2Stagger, () => { if (lws[6+i]) lws[6+i].classList.add('visible') })
  }
  after(T.p2Start, () => { if (spacerLineEl.value) spacerLineEl.value.classList.add('visible') })

  // Etymology labels
  after(T.labelsIn, () => { if (labelsEl.value) labelsEl.value.classList.add('visible') })

  // Dim the letters that will vanish
  after(T.dimStart, () => {
    fadeIds.forEach(i => { if (lws[i]) lws[i].classList.add('dimmed') })
  })

  // Collapse to IREKAI + fade labels simultaneously
  after(T.collapseStart, () => {
    if (spacerLineEl.value) spacerLineEl.value.classList.remove('visible')
    if (spacerEl.value) spacerEl.value.classList.add('collapse')
    fadeIds.forEach(i => { if (lws[i]) lws[i].classList.add('collapse') })
    if (labelsEl.value) labelsEl.value.classList.remove('visible')
  })

  // Seal appears then draws
  after(T.sealIn, () => {
    if (sealEl.value) {
      sealEl.value.classList.add('visible')
      setTimeout(() => { if (sealEl.value) sealEl.value.classList.add('drawing') }, 400)
    }
  })

  // Tagline
  after(T.tagIn, () => { if (taglineEl.value) taglineEl.value.classList.add('visible') })

}

onMounted(() => { setTimeout(run, 300) })
onUnmounted(() => { timers.forEach(clearTimeout) })

// ── Why IREKAI items ─────────────────────────────────────────────────
const whyItems = [
  {
    title: 'Built for practitioners',
    body: 'Every framework and tool has been designed to offer real-world migration assistance.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg>`
  },
  {
    title: 'End-to-end coverage',
    body: 'From the first boardroom conversation to continuous post-migration monitoring — IREKAI covers the full quantum transition lifecycle.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="10"/><path d="M12 6v6l4 2"/></svg>`
  },
  {
    title: 'Standards-aligned',
    body: 'Aligned with FIPS 203/204/205, CNSA 2.0, NIS2, ISO 27001, and emerging EU regulations. Your compliance evidence is built in.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>`
  },
  {
    title: 'Actionable, not theoretical',
    body: 'No lengthy consulting engagements that end in a shelf report. IREKAI delivers tools and actionable advice you can use today.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>`
  },
]
</script>

<style scoped>
/* ── Hero layout ──────────────────────────────────────────────────── */
.hero-section {
  min-height: 100svh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem 1.5rem;
  position: relative;
  overflow: hidden;
}

.hero-center {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  padding-top: 210px;
  position: relative;
}

/* ── Seal ─────────────────────────────────────────────────────────── */
.seal-area {
  position: absolute;
  top: 8px;
  left: 50%;
  transform: translateX(-50%) translateY(10px) scale(0.88);
  opacity: 0;
  transition: opacity 0.55s ease, transform 0.65s cubic-bezier(.2,0,.2,1);
}
.seal-area.visible {
  opacity: 1;
  transform: translateX(-50%) translateY(0) scale(1);
}

.seal-rect-outer { stroke-dasharray: 576; stroke-dashoffset: 576; }
.seal-area.drawing .seal-rect-outer {
  animation: drawStroke 1.1s cubic-bezier(.4,0,.2,1) 0s forwards;
}
.seal-corners { opacity: 0; }
.seal-area.drawing .seal-corners { animation: fadeInEl 0.4s ease 0.9s forwards; }
.seal-lattice { opacity: 0; }
.seal-area.drawing .seal-lattice { animation: fadeInEl 0.5s ease 0.85s forwards; }
.seal-rect-inner { stroke-dasharray: 256; stroke-dashoffset: 256; }
.seal-area.drawing .seal-rect-inner {
  animation: drawStroke 0.6s cubic-bezier(.4,0,.2,1) 1.0s forwards;
}
.seal-axes { opacity: 0; }
.seal-area.drawing .seal-axes { animation: fadeInEl 0.35s ease 1.4s forwards; }
.seal-ring { stroke-dasharray: 41; stroke-dashoffset: 41; }
.seal-area.drawing .seal-ring { animation: drawStroke 0.35s ease 1.55s forwards; }
.seal-dot { transform-origin: 100px 100px; transform: scale(0); }
.seal-area.drawing .seal-dot {
  animation: dotPop 0.28s cubic-bezier(.2,0,.2,1) 1.85s forwards;
}

@keyframes drawStroke { to { stroke-dashoffset: 0; } }
@keyframes fadeInEl   { to { opacity: 1; } }
@keyframes dotPop     { to { transform: scale(1); } }

/* ── Name row ─────────────────────────────────────────────────────── */
.name-area {
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-weight: 500;
  font-size: clamp(72px, 9.5vw, 120px);
  text-transform: uppercase;
  line-height: 1;
  white-space: nowrap;
  letter-spacing: 0.04em;
}

.lw {
  display: block;
  overflow: hidden;
  max-width: 1.2em;
  transition:
    max-width 0.52s cubic-bezier(.4,0,.2,1) 0.22s,
    opacity   0.22s ease 0s;
}
.lt {
  display: block;
  padding: 0 0.06em;
  opacity: 0;
  color: var(--text);
  transition: opacity 0.28s ease;
}
.lw.visible .lt        { opacity: 1; }
.lw.fade.dimmed .lt    { opacity: 0.13; }
.lw.collapse           { max-width: 0; }
.lw.collapse .lt       { opacity: 0; }

/* Spacer */
.lw.spacer {
  max-width: 8em;
  display: flex;
  align-items: center;
  justify-content: center;
  transition:
    max-width 0.44s cubic-bezier(.4,0,.2,1) 0.04s,
    opacity   0.22s ease 0s;
}
.lw.spacer.collapse { max-width: 0; }

.spacer-line {
  display: block;
  width: 1px;
  height: 0.6em;
  background: var(--text-dim);
  opacity: 0;
  flex-shrink: 0;
  transition: opacity 0.5s ease;
}
.spacer-line.visible { opacity: 0.55; }

/* ── Below area ───────────────────────────────────────────────────── */
.below-area {
  position: relative;
  margin-top: 32px;
  min-height: 52px;
  width: 100%;
  display: flex;
  align-items: flex-start;
  justify-content: center;
}

.labels-row {
  position: absolute;
  display: flex;
  gap: clamp(44px, 6.5vw, 88px);
  align-items: flex-start;
  opacity: 0;
  transition: opacity 0.5s ease;
}
.labels-row.visible { opacity: 1; }

.word-label { display: flex; flex-direction: column; align-items: center; gap: 5px; }

.lbl-glyph {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-weight: 400;
  font-size: clamp(17px, 2.2vw, 26px);
  color: #7aad97;
  opacity: 0.72;
  letter-spacing: 0.03em;
}
.lbl-meaning {
  font-family: var(--font-mono);
  font-weight: 300;
  font-size: clamp(9px, 1.1vw, 13px);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--text-dim);
  opacity: 0.55;
}

.hero-tagline {
  position: absolute;
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-style: italic;
  font-weight: 300;
  font-size: clamp(16px, 2vw, 22px);
  color: var(--text-muted);
  letter-spacing: 0.01em;
  opacity: 0;
  text-align: center;
  transition: opacity 0.6s ease;
}
.hero-tagline.visible { opacity: 1; }

/* ── Products section ─────────────────────────────────────────────── */
.products-section { padding: 5rem 0 6rem; }

.section-head { display: flex; flex-direction: column; gap: 1rem; margin-bottom: 3rem; }
.section-title { font-size: clamp(1.8rem, 4vw, 2.8rem); font-weight: 500; line-height: 1.15; color: var(--text); }
.section-sub { font-size: 0.95rem; line-height: 1.7; color: var(--text-muted); max-width: 56ch; }

.products-grid { display: grid; grid-template-columns: 1fr; gap: 1.25rem; }
@media (min-width: 640px)  { .products-grid { grid-template-columns: 1fr 1fr; } }
@media (min-width: 1024px) {
  .products-grid { grid-template-columns: 1fr 1fr 1fr; }
  .product-card--featured { grid-column: span 2; }
}

.product-card {
  display: flex; flex-direction: column; gap: 1rem;
  padding: 1.75rem; border-radius: 14px; border: 1px solid var(--border);
  background: rgba(28,25,23,0.5); text-decoration: none; color: inherit;
  transition: border-color 0.2s, background 0.2s, box-shadow 0.2s, transform 0.2s;
  position: relative; overflow: hidden;
}
.product-card::before {
  content: ''; position: absolute; inset: 0;
  background: radial-gradient(ellipse at top left, var(--card-glow, transparent) 0%, transparent 70%);
  pointer-events: none; opacity: 0; transition: opacity 0.3s;
}
.product-card:hover::before { opacity: 1; }
.product-card:hover { transform: translateY(-2px); }

.product-card.sage   { --card-glow: rgba(122,173,151,0.08); --accent: #7aad97; }
.product-card.sage:hover   { border-color: rgba(122,173,151,0.45); box-shadow: 0 8px 40px -12px rgba(122,173,151,0.25); }
.product-card.amber  { --card-glow: rgba(251,191,36,0.08);  --accent: var(--amber); }
.product-card.amber:hover  { border-color: rgba(251,191,36,0.45);  box-shadow: 0 8px 40px -12px rgba(251,191,36,0.2); }
.product-card.violet { --card-glow: rgba(167,139,250,0.08); --accent: var(--violet); }
.product-card.violet:hover { border-color: rgba(167,139,250,0.45); box-shadow: 0 8px 40px -12px rgba(167,139,250,0.2); }
.product-card.fuchsia{ --card-glow: rgba(232,121,249,0.08); --accent: var(--fuchsia); }
.product-card.fuchsia:hover{ border-color: rgba(232,121,249,0.45); box-shadow: 0 8px 40px -12px rgba(232,121,249,0.2); }

.card-badge { font-family: var(--font-mono); font-size: 0.62rem; letter-spacing: 0.15em; text-transform: uppercase; padding: 0.25rem 0.65rem; border-radius: 4px; display: inline-flex; align-self: flex-start; }
.sage-badge { background: rgba(122,173,151,0.1); color: #7aad97; border: 1px solid rgba(122,173,151,0.3); }

.card-icon { width: 40px; height: 40px; display: flex; align-items: center; justify-content: center; border-radius: 8px; background: rgba(255,255,255,0.04); border: 1px solid var(--border); color: var(--accent, var(--text-muted)); flex-shrink: 0; }
.card-icon svg { width: 20px; height: 20px; }
.card-title { font-family: var(--font-display); font-size: 1.15rem; font-weight: 500; color: var(--text); line-height: 1.3; }
.product-card--featured .card-title { font-size: 1.4rem; }
.card-desc { font-size: 0.875rem; line-height: 1.7; color: var(--text-muted); flex: 1; }
.card-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
.card-cta { font-family: var(--font-mono); font-size: 0.72rem; letter-spacing: 0.05em; color: var(--accent, var(--text-muted)); display: flex; align-items: center; gap: 0.35rem; margin-top: 0.25rem; }
.arrow { transition: transform 0.15s; }
.product-card:hover .arrow { transform: translateX(4px); }

/* ── Why IREKAI ───────────────────────────────────────────────────── */
.why-section { padding: 4rem 0; border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }
.why-grid { display: grid; grid-template-columns: 1fr; gap: 2rem; }
@media (min-width: 640px)  { .why-grid { grid-template-columns: 1fr 1fr; } }
@media (min-width: 1024px) { .why-grid { grid-template-columns: repeat(4, 1fr); } }
.why-item  { display: flex; flex-direction: column; gap: 0.85rem; }
.why-icon  { width: 34px; height: 34px; color: #7aad97; opacity: 0.8; }
.why-icon svg { width: 100%; height: 100%; }
.why-title { font-family: var(--font-display); font-size: 1rem; color: var(--text); margin-bottom: 0.3rem; }
.why-body  { font-size: 0.85rem; line-height: 1.7; color: var(--text-muted); }

/* ── CTA Banner ───────────────────────────────────────────────────── */
.cta-section { padding: 5rem 0; }
.cta-inner { display: flex; flex-direction: column; gap: 2rem; align-items: flex-start; }
@media (min-width: 768px) { .cta-inner { flex-direction: row; align-items: center; justify-content: space-between; } }
.cta-text { flex: 1; }
.cta-actions { display: flex; flex-wrap: wrap; gap: 0.75rem; flex-shrink: 0; }

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
</style>
