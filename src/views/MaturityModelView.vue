<template>
  <div>
    <section class="product-hero">
      <div class="container">
        <div class="hero-top">
          <RouterLink to="/" class="breadcrumb">← Back to home</RouterLink>
          <span class="badge" style="background:rgba(251,191,36,0.1);color:#fbbf24;border-color:rgba(251,191,36,0.35);">
            Framework
          </span>
        </div>

        <div class="hero-body">
          <div class="hero-text">
            <div class="section-label" style="margin-bottom:1rem;color:#fbbf24;opacity:0.85;">
              02 · PQC Migration Maturity Model
            </div>
            <h1 class="hero-h1 font-display">
              Five tiers. Five dimensions.<br/>
              <em style="color:#fbbf24">One clear path.</em>
            </h1>
            <p class="hero-lead">
              The IREKAI PQC Migration Maturity Model gives you a structured, holistic view of your
              cryptographic posture — from initial awareness to continuous quantum-safe operations.
              Each tier builds on the last, with concrete activities and measurable outcomes.
            </p>
            <div class="hero-actions">
              <button @click="openForm" class="btn" style="background:rgba(251,191,36,0.1);border-color:rgba(251,191,36,0.4);color:#fbbf24;font-size:0.8rem;padding:0.75rem 1.6rem;cursor:pointer;">
                Get the framework →
              </button>
              <a href="mailto:info@irekai.nl" class="btn btn-ghost" style="font-size:0.8rem;padding:0.75rem 1.5rem;">
                Book a demo
              </a>
            </div>
          </div>

          <!-- Mini tier preview -->
          <div class="tier-preview-card">
            <div class="font-mono tier-label">Maturity tiers</div>
            <div class="tiers-mini">
              <div class="tier-mini" v-for="t in tiers" :key="t.name" :class="t.state">
                <div class="tier-num font-mono">{{ String(t.n).padStart(2,'0') }}</div>
                <div>
                  <div class="tier-name font-display">{{ t.name }}</div>
                  <div class="tier-sub">{{ t.sub }}</div>
                </div>
                <div class="tier-risk" :class="`risk-${t.risk}`">{{ t.risk }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Dimensions -->
    <section class="dims-section">
      <div class="container">
        <div class="section-label" style="margin-bottom:1.5rem;">Five cryptographic dimensions</div>
        <div class="dims-grid">
          <div class="dim-card" v-for="d in dims" :key="d.code" :style="`--c:${d.color}`">
            <div class="dim-code font-mono">{{ d.code }}</div>
            <div class="dim-name font-display">{{ d.name }}</div>
            <div class="dim-blurb">{{ d.blurb }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- What it provides -->
    <section class="value-section">
      <div class="container">
        <div class="two-col">
          <div>
            <div class="section-label" style="margin-bottom:1.25rem;">What the model provides</div>
            <div class="value-list">
              <div class="value-item" v-for="v in values" :key="v">
                <div class="value-dot"></div>
                <span>{{ v }}</span>
              </div>
            </div>
          </div>
          <div>
            <div class="section-label" style="margin-bottom:1.25rem;">How organisations use it</div>
            <div class="use-list">
              <div class="use-item" v-for="u in uses" :key="u.title">
                <div class="use-title">{{ u.title }}</div>
                <div class="use-body">{{ u.body }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Tech tree teaser — interactive embed -->
    <section class="teaser-section">
      <div class="container">
        <div class="teaser-header">
          <div class="badge amber-badge">Interactive preview</div>
          <h3 class="font-display" style="font-size:1.3rem;color:var(--text);margin-top:0.75rem;margin-bottom:0.5rem;">
            PQC Migration Tech Tree
          </h3>
          <p class="prose" style="max-width:56ch;">
            A live preview of the maturity model — 104 activities across 5 dimensions and 5 tiers,
            with a dependency map showing which steps unlock which.
            <span style="color:var(--text-dim);font-size:0.8em;"> Fill in your details below to unlock the full interactive version.</span>
          </p>
        </div>

        <div class="teaser-frame-wrap">
          <iframe
            src="/assets/pqc-teaser.html"
            class="teaser-frame"
            title="PQC Migration Tech Tree — interactive preview"
            loading="lazy"
            scrolling="no"
          ></iframe>
          <div class="teaser-overlay">
            <div class="teaser-overlay-inner">
              <p class="font-mono" style="font-size:0.7rem;letter-spacing:0.15em;text-transform:uppercase;color:var(--text-dim);margin-bottom:0.75rem;">Full access — free</p>
              <button @click="openForm" class="btn" style="background:rgba(251,191,36,0.1);border-color:rgba(251,191,36,0.4);color:#fbbf24;font-size:0.8rem;padding:0.7rem 1.5rem;cursor:pointer;">
                Get full access →
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Access form modal -->
    <Transition name="modal">
      <div v-if="formOpen" class="modal-backdrop" @click.self="closeForm">
        <div class="modal-card">

          <!-- Not yet submitted -->
          <template v-if="!formDone">
            <button class="modal-close" @click="closeForm" aria-label="Close">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
            </button>
            <div class="modal-label font-mono">Free access</div>
            <h3 class="modal-heading font-display">Get the PQC Maturity Model</h3>
            <p class="modal-sub">Fill in your details and the framework is yours immediately.</p>

            <form class="access-form" @submit.prevent="submitForm">
              <div class="form-row">
                <div class="form-field">
                  <label class="form-label">Name</label>
                  <input v-model="form.name" type="text" class="form-input" placeholder="Jane Smith" required />
                </div>
                <div class="form-field">
                  <label class="form-label">Job title</label>
                  <input v-model="form.title" type="text" class="form-input" placeholder="CISO" required />
                </div>
              </div>
              <div class="form-field">
                <label class="form-label">Company</label>
                <input v-model="form.company" type="text" class="form-input" placeholder="Acme Corp" required />
              </div>
              <div class="form-field">
                <label class="form-label">Work email</label>
                <input v-model="form.email" type="email" class="form-input" placeholder="jane@acme.com" required />
              </div>
              <button type="submit" class="btn form-submit-btn">
                Get instant access →
              </button>
            </form>
          </template>

          <!-- Submitted — show download -->
          <template v-else>
            <div class="modal-success">
              <div class="success-icon">
                <svg viewBox="0 0 24 24" fill="none" stroke="#fbbf24" stroke-width="1.5">
                  <path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/>
                  <polyline points="22 4 12 14.01 9 11.01"/>
                </svg>
              </div>
              <h3 class="modal-heading font-display">You're in, {{ form.name.split(' ')[0] }}.</h3>
              <p class="modal-sub">Your copy of the IREKAI PQC Migration Maturity Model is ready.</p>
              <a :href="docUrl" download class="btn form-submit-btn" style="text-align:center;justify-content:center;">
                ↓ Download framework
              </a>
              <p class="modal-note">
                A copy will also be sent to {{ form.email }} within 24 hours.
              </p>
              <button class="modal-close-text font-mono" @click="closeForm">Close</button>
            </div>
          </template>

        </div>
      </div>
    </Transition>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const tiers = [
  { n:1, name:'Initial',   sub:'Awareness & first steps',    risk:'critical', state:'t-done' },
  { n:2, name:'Basic',     sub:'Processes & tooling',        risk:'high',     state:'t-active' },
  { n:3, name:'Advanced',  sub:'Implementation underway',    risk:'medium',   state:'' },
  { n:4, name:'Managed',   sub:'Systematic control',         risk:'low',      state:'' },
  { n:5, name:'Optimised', sub:'Continuous excellence',      risk:'minimal',  state:'' },
]

const dims = [
  { code:'01', name:'Crypto Agility',      color:'#e879f9', blurb:'Swap algorithms without rewriting systems. Modular design, enforced CI/CD policies, and config-driven crypto.' },
  { code:'02', name:'Asset Inventory',     color:'#22d3ee', blurb:'Know what cryptographic assets you have, where they are, and which are quantum-vulnerable.' },
  { code:'03', name:'PQC Availability',    color:'#34d399', blurb:'Post-quantum algorithms available, approved, and deployed — from test environments to production default.' },
  { code:'04', name:'Governance',          color:'#fbbf24', blurb:'Policy, ownership, budget, and compliance. The framework that drives and sustains the entire migration.' },
  { code:'05', name:'Supplier Management', color:'#a78bfa', blurb:'Extend quantum-readiness beyond your own estate. Assess vendors, embed PQC requirements in contracts.' },
]

const values = [
  'A shared language for cryptographic maturity across teams and leadership',
  '104 concrete activities mapped to maturity tiers and dimensions',
  'Built-in dependency graph — see which activities unlock which',
  'Risk profile at each tier across quantum, supply chain, compliance, and operational axes',
  'Alignment with NIST, BSI, ETSI, NIS2, ISO 27001, and CNSA 2.0',
  'Export and import of organisational progress for reporting',
]

const uses = [
  { title: 'Baseline assessment', body: 'Map your current state in a structured workshop. Identify where you are on each dimension without guesswork.' },
  { title: 'Roadmap creation',    body: 'Use tier requirements and the dependency graph to plan a realistic, sequenced migration roadmap.' },
  { title: 'Board reporting',     body: 'Translate technical progress into a single maturity score and risk-reduction narrative for leadership.' },
  { title: 'Procurement',         body: 'Define quantum-readiness requirements for vendors and use the model to evaluate their responses.' },
]

// ── Access form ──────────────────────────────────────────────────────────────

// Replace with actual asset path when document is ready
const docUrl = '/assets/irekai-pqc-maturity-model.pdf'

const formOpen = ref(false)
const formDone = ref(false)
const form = reactive({ name: '', title: '', company: '', email: '' })

function openForm() { formOpen.value = true; formDone.value = false }
function closeForm() { formOpen.value = false }

function submitForm() {
  // Notify IREKAI via pre-filled email (fires silently in background)
  const subject = encodeURIComponent(`Maturity Model Download — ${form.company}`)
  const body = encodeURIComponent(
    `New maturity model download:\n\nName: ${form.name}\nJob title: ${form.title}\nCompany: ${form.company}\nEmail: ${form.email}`
  )
  const mailto = `mailto:info@irekai.nl?subject=${subject}&body=${body}`
  const a = document.createElement('a')
  a.href = mailto
  a.click()

  formDone.value = true
}
</script>

<style scoped>
.hero-top { display: flex; align-items: center; justify-content: space-between; margin-bottom: 2.5rem; flex-wrap: wrap; gap: 1rem; }
.breadcrumb { font-family: var(--font-mono); font-size: 0.72rem; color: var(--text-dim); text-decoration: none; transition: color 0.15s; }
.breadcrumb:hover { color: var(--text-muted); }

.hero-body { display: grid; grid-template-columns: 1fr; gap: 3rem; align-items: flex-start; }
@media (min-width: 900px) { .hero-body { grid-template-columns: 1fr 360px; } }

.hero-h1 { font-size: clamp(1.9rem, 5vw, 3rem); font-weight: 500; line-height: 1.15; color: var(--text); margin-bottom: 1.25rem; }
.hero-lead { font-size: 1rem; line-height: 1.75; color: var(--text-muted); max-width: 56ch; margin-bottom: 2rem; }
.hero-actions { display: flex; flex-wrap: wrap; gap: 0.75rem; }

/* Tier preview */
.tier-preview-card { background: rgba(28,25,23,0.7); border: 1px solid var(--border); border-radius: 14px; padding: 1.5rem; }
.tier-label { font-size: 0.62rem; letter-spacing: 0.18em; text-transform: uppercase; color: var(--text-dim); margin-bottom: 1rem; }
.tiers-mini { display: flex; flex-direction: column; gap: 0.6rem; }
.tier-mini { display: grid; grid-template-columns: 2rem 1fr auto; align-items: center; gap: 0.75rem; padding: 0.6rem 0.75rem; border-radius: 8px; border: 1px solid transparent; opacity: 0.45; }
.tier-mini.t-done { border-color: rgba(52,211,153,0.25); background: rgba(52,211,153,0.05); opacity: 1; }
.tier-mini.t-active { border-color: rgba(251,191,36,0.35); background: rgba(251,191,36,0.05); opacity: 1; }
.tier-num { font-size: 0.6rem; color: var(--text-dim); }
.tier-name { font-size: 0.85rem; color: var(--text); }
.tier-sub { font-size: 0.7rem; color: var(--text-dim); margin-top: 1px; }
.tier-risk { font-family: var(--font-mono); font-size: 0.58rem; letter-spacing: 0.1em; text-transform: uppercase; padding: 0.15rem 0.45rem; border-radius: 3px; white-space: nowrap; }
.risk-critical { background: rgba(239,68,68,0.12); color: #f87171; }
.risk-high     { background: rgba(249,115,22,0.12); color: #fb923c; }
.risk-medium   { background: rgba(234,179,8,0.12);  color: #facc15; }
.risk-low      { background: rgba(132,204,22,0.12); color: #a3e635; }
.risk-minimal  { background: rgba(52,211,153,0.12); color: #34d399; }

/* Dimensions */
.dims-section { padding: 4rem 0; border-top: 1px solid var(--border); }
.dims-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(210px, 1fr)); gap: 1rem; }
.dim-card { padding: 1.25rem; border-radius: 10px; border: 1px solid rgba(255,255,255,0.06); background: rgba(28,25,23,0.5); transition: border-color 0.2s; }
.dim-card:hover { border-color: var(--c); }
.dim-code { font-size: 0.6rem; letter-spacing: 0.2em; color: var(--c); margin-bottom: 0.5rem; }
.dim-name { font-size: 0.95rem; color: var(--text); margin-bottom: 0.5rem; }
.dim-blurb { font-size: 0.78rem; line-height: 1.6; color: var(--text-muted); }

/* Value section */
.value-section { padding: 4rem 0; border-top: 1px solid var(--border); }
.two-col { display: grid; grid-template-columns: 1fr; gap: 3rem; }
@media (min-width: 768px) { .two-col { grid-template-columns: 1fr 1fr; } }

.value-list { display: flex; flex-direction: column; gap: 0.8rem; }
.value-item { display: flex; align-items: flex-start; gap: 0.65rem; font-size: 0.875rem; line-height: 1.6; color: var(--text-muted); }
.value-dot { width: 5px; height: 5px; border-radius: 50%; background: #fbbf24; flex-shrink: 0; margin-top: 0.55rem; opacity: 0.8; }

.use-list { display: flex; flex-direction: column; gap: 1.25rem; }
.use-title { font-size: 0.9rem; font-weight: 500; color: var(--text); margin-bottom: 0.25rem; }
.use-body { font-size: 0.82rem; line-height: 1.6; color: var(--text-muted); }

/* Teaser section */
.teaser-section { padding: 3rem 0 5rem; }
.teaser-header { margin-bottom: 1.5rem; }
.teaser-frame-wrap { position: relative; border-radius: 14px; overflow: hidden; border: 1px solid rgba(251,191,36,0.2); background: #0c0a09; height: clamp(400px, 60vw, 600px); }
.teaser-frame { width: 100%; height: 100%; border: none; display: block; pointer-events: none; }
.teaser-overlay { position: absolute; bottom: 0; left: 0; right: 0; height: 120px; background: linear-gradient(to bottom, transparent, rgba(12,10,9,0.92) 60%); display: flex; align-items: flex-end; justify-content: center; padding-bottom: 1.75rem; }
.teaser-overlay-inner { display: flex; flex-direction: column; align-items: center; gap: 0.5rem; }
.amber-badge { background: rgba(251,191,36,0.1); color: #fbbf24; border-color: rgba(251,191,36,0.3); }

/* ── Access form modal ─────────────────────────────────────────── */
.modal-backdrop {
  position: fixed;
  inset: 0;
  background: rgba(12,10,9,0.82);
  backdrop-filter: blur(6px);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 999;
  padding: 1.5rem;
}

.modal-card {
  background: #1a1714;
  border: 1px solid rgba(251,191,36,0.25);
  border-radius: 16px;
  padding: 2.25rem 2.5rem;
  width: 100%;
  max-width: 480px;
  position: relative;
}

.modal-close {
  position: absolute;
  top: 1.1rem;
  right: 1.1rem;
  width: 28px; height: 28px;
  background: transparent;
  border: none;
  cursor: pointer;
  color: var(--text-dim);
  transition: color 0.15s;
  padding: 0;
  display: flex; align-items: center; justify-content: center;
}
.modal-close:hover { color: var(--text); }
.modal-close svg { width: 16px; height: 16px; }

.modal-label { font-size: 0.6rem; letter-spacing: 0.2em; text-transform: uppercase; color: #fbbf24; opacity: 0.8; margin-bottom: 0.75rem; }
.modal-heading { font-size: 1.35rem; font-weight: 500; color: var(--text); margin-bottom: 0.5rem; }
.modal-sub { font-size: 0.85rem; line-height: 1.65; color: var(--text-muted); margin-bottom: 1.75rem; }

/* Form */
.access-form { display: flex; flex-direction: column; gap: 1rem; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
@media (max-width: 480px) { .form-row { grid-template-columns: 1fr; } }

.form-field { display: flex; flex-direction: column; gap: 0.4rem; }
.form-label { font-family: var(--font-mono); font-size: 0.65rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--text-dim); }
.form-input {
  background: rgba(255,255,255,0.04);
  border: 1px solid var(--border);
  border-radius: 7px;
  padding: 0.6rem 0.85rem;
  font-family: var(--font-mono);
  font-size: 0.8rem;
  color: var(--text);
  outline: none;
  transition: border-color 0.15s;
  width: 100%;
  box-sizing: border-box;
}
.form-input::placeholder { color: var(--text-dim); }
.form-input:focus { border-color: rgba(251,191,36,0.5); }

.form-submit-btn {
  background: rgba(251,191,36,0.12);
  border: 1px solid rgba(251,191,36,0.45);
  color: #fbbf24;
  font-family: var(--font-mono);
  font-size: 0.8rem;
  padding: 0.8rem 1.5rem;
  border-radius: 7px;
  cursor: pointer;
  transition: all 0.2s;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  text-decoration: none;
  margin-top: 0.5rem;
}
.form-submit-btn:hover { background: rgba(251,191,36,0.2); border-color: rgba(251,191,36,0.7); box-shadow: 0 0 20px -6px rgba(251,191,36,0.4); }

/* Success state */
.modal-success { display: flex; flex-direction: column; align-items: center; text-align: center; gap: 0.75rem; padding: 0.5rem 0; }
.success-icon { width: 48px; height: 48px; border-radius: 50%; background: rgba(251,191,36,0.08); border: 1px solid rgba(251,191,36,0.25); display: flex; align-items: center; justify-content: center; margin-bottom: 0.5rem; }
.success-icon svg { width: 24px; height: 24px; }
.modal-note { font-size: 0.75rem; color: var(--text-dim); line-height: 1.6; max-width: 34ch; }
.modal-close-text { background: none; border: none; cursor: pointer; font-size: 0.65rem; letter-spacing: 0.1em; color: var(--text-dim); padding: 0; transition: color 0.15s; margin-top: 0.5rem; }
.modal-close-text:hover { color: var(--text-muted); }

/* Modal transition */
.modal-enter-active, .modal-leave-active { transition: opacity 0.2s ease; }
.modal-enter-active .modal-card, .modal-leave-active .modal-card { transition: transform 0.25s cubic-bezier(.2,0,.2,1), opacity 0.2s ease; }
.modal-enter-from, .modal-leave-to { opacity: 0; }
.modal-enter-from .modal-card, .modal-leave-to .modal-card { transform: translateY(16px) scale(0.97); opacity: 0; }
</style>
