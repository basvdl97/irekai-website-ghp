<template>
  <div>
    <!-- Hero -->
    <section class="product-hero" style="--accent:#2dd4bf;--accent-soft:rgba(45,212,191,0.08);">
      <div class="container">
        <div class="hero-top">
          <RouterLink to="/" class="breadcrumb">← Back to home</RouterLink>
          <span class="badge" style="background:rgba(45,212,191,0.1);color:#2dd4bf;border-color:rgba(45,212,191,0.35);">
            Flagship product
          </span>
        </div>

        <div class="hero-body">
          <div class="hero-text">
            <div class="section-label" style="margin-bottom:1rem;color:#2dd4bf;opacity:0.8;">
              01 · Quantum Readiness Assessment
            </div>
            <h1 class="hero-h1 font-display">
              Know your quantum<br/>
              <em style="color:#2dd4bf">exposure. Now.</em>
            </h1>
            <p class="hero-lead">
              IREKAI's Quantum Readiness Assessment gives organisations a clear, actionable
              picture of their cryptographic posture — in 4–6 weeks, not months. Our specialists
              do the heavy lifting: you get sharp insight and a prioritised roadmap.
            </p>
            <div class="hero-actions">
              <a href="mailto:info@irekai.nl?subject=Quantum Readiness Assessment" class="btn btn-teal" style="font-size:0.8rem;padding:0.75rem 1.6rem;">
                Request your assessment →
              </a>
            </div>
          </div>

          <div class="hero-visual">
            <div class="readiness-dial-card">
              <div class="dial-label font-mono">Sample output</div>
              <div class="dial-rings">
                <svg viewBox="0 0 120 120" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <circle cx="60" cy="60" r="54" stroke="rgba(41,37,36,1)" stroke-width="12"/>
                  <circle cx="60" cy="60" r="54" stroke="#2dd4bf" stroke-width="12"
                          stroke-dasharray="339.3" stroke-dashoffset="220.5"
                          stroke-linecap="round" transform="rotate(-90 60 60)"
                          style="filter:drop-shadow(0 0 6px rgba(45,212,191,0.6))"/>
                  <text x="60" y="56" text-anchor="middle" font-family="'Fraunces',Georgia,serif"
                        font-size="20" fill="#e7e5e4">35</text>
                  <text x="60" y="70" text-anchor="middle" font-family="'JetBrains Mono',monospace"
                        font-size="7" fill="#78716c" letter-spacing="1">/ 100</text>
                </svg>
              </div>
              <div class="dial-legend">
                <div class="dial-legend-row" v-for="d in dialItems" :key="d.label">
                  <div class="dial-dot" :style="`background:${d.color}`"></div>
                  <span class="dial-name">{{ d.label }}</span>
                  <span class="dial-score" :style="`color:${d.color}`">{{ d.score }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- What you get -->
    <section class="content-section">
      <div class="container">
        <div class="two-col">
          <div>
            <div class="section-label" style="margin-bottom:1.25rem;">What you get</div>
            <div class="deliverable-list">
              <div class="deliverable" v-for="d in deliverables" :key="d.title">
                <div class="deliverable-icon" style="color:#2dd4bf;">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M9 12l2 2 4-4"/>
                    <circle cx="12" cy="12" r="10"/>
                  </svg>
                </div>
                <div>
                  <div class="deliverable-title">{{ d.title }}</div>
                  <div class="deliverable-body">{{ d.body }}</div>
                </div>
              </div>
            </div>
          </div>
          <div>
            <div class="section-label" style="margin-bottom:1.25rem;">How it works</div>
            <div class="steps">
              <div class="step" v-for="(s, i) in steps" :key="i">
                <div class="step-num font-mono">{{ String(i+1).padStart(2,'0') }}</div>
                <div>
                  <div class="step-title">{{ s.title }}</div>
                  <div class="step-body">{{ s.body }}</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Areas covered -->
    <section class="areas-section">
      <div class="container">
        <div class="section-label" style="margin-bottom:1.5rem;">Assessment dimensions</div>
        <div class="areas-grid">
          <div class="area-card" v-for="a in areas" :key="a.name" :style="`--c:${a.color}`">
            <div class="area-code font-mono">{{ a.code }}</div>
            <div class="area-name font-display">{{ a.name }}</div>
            <div class="area-desc">{{ a.desc }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Intake questionnaire -->
    <section class="intake-section">
      <div class="container">

        <div class="intake-intro" v-if="step === 0">
          <div class="badge" style="background:rgba(45,212,191,0.1);color:#2dd4bf;border-color:rgba(45,212,191,0.3);margin-bottom:1.25rem;">
            Quick readiness profile
          </div>
          <h3 class="font-display intake-heading">
            Not sure where to start?<br/>
            <em style="color:#2dd4bf">Tell us about your situation.</em>
          </h3>
          <p class="intake-lead">
            Answer five quick questions and get a rough readiness profile. We'll use your answers
            to tailor our approach — and reach back with a concrete proposal that fits your organisation.
          </p>
          <button class="btn btn-teal intake-start-btn" @click="step = 1">
            Get my quick profile →
          </button>
        </div>

        <div class="intake-flow" v-else>

          <!-- Progress indicator -->
          <div class="intake-progress">
            <div class="progress-step" :class="{active: step >= 1, done: step > 1}">
              <div class="progress-dot">
                <svg v-if="step > 1" viewBox="0 0 12 12" fill="none"><polyline points="2,6 5,9 10,3" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
                <span v-else>1</span>
              </div>
              <span class="progress-label">Profile</span>
            </div>
            <div class="progress-line" :class="{active: step > 1}"></div>
            <div class="progress-step" :class="{active: step >= 2, done: step > 2}">
              <div class="progress-dot">
                <svg v-if="step > 2" viewBox="0 0 12 12" fill="none"><polyline points="2,6 5,9 10,3" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
                <span v-else>2</span>
              </div>
              <span class="progress-label">Self-rating</span>
            </div>
            <div class="progress-line" :class="{active: step > 2}"></div>
            <div class="progress-step" :class="{active: step >= 3}">
              <div class="progress-dot"><span>3</span></div>
              <span class="progress-label">Your profile</span>
            </div>
          </div>

          <!-- Step 1: Organisation profile -->
          <div class="intake-card" v-if="step === 1">
            <div class="intake-card-label font-mono">Step 1 of 2 — Organisation profile</div>
            <h4 class="intake-card-heading font-display">Tell us about your organisation</h4>

            <div class="intake-field">
              <div class="intake-field-label">Sector</div>
              <div class="pill-group">
                <button
                  v-for="s in sectors" :key="s"
                  class="pill"
                  :class="{ selected: profile.sector === s }"
                  @click="profile.sector = s"
                >{{ s }}</button>
              </div>
            </div>

            <div class="intake-field">
              <div class="intake-field-label">Organisation size</div>
              <div class="pill-group">
                <button
                  v-for="sz in sizes" :key="sz"
                  class="pill"
                  :class="{ selected: profile.size === sz }"
                  @click="profile.size = sz"
                >{{ sz }}</button>
              </div>
            </div>

            <div class="intake-field">
              <div class="intake-field-label">Primary driver for quantum-readiness</div>
              <div class="pill-group">
                <button
                  v-for="d in drivers" :key="d"
                  class="pill"
                  :class="{ selected: profile.driver === d }"
                  @click="profile.driver = d"
                >{{ d }}</button>
              </div>
            </div>

            <div class="intake-card-footer">
              <button class="btn btn-ghost intake-back" @click="step = 0">← Back</button>
              <button
                class="btn btn-teal"
                style="font-size:0.8rem;padding:0.7rem 1.5rem;"
                :disabled="!profileDone"
                @click="step = 2"
              >Continue →</button>
            </div>
          </div>

          <!-- Step 2: Dimension self-rating -->
          <div class="intake-card" v-else-if="step === 2">
            <div class="intake-card-label font-mono">Step 2 of 2 — Dimension self-rating</div>
            <h4 class="intake-card-heading font-display">How would you rate each area?</h4>
            <p class="intake-subtext">Be honest — this is just a rough indicator. 1 = not started, 5 = well advanced.</p>

            <div class="ratings-list">
              <div class="rating-row" v-for="dim in dimDefs" :key="dim.name">
                <div class="rating-row-left">
                  <span class="rating-dim-dot" :style="`background:${dim.color}`"></span>
                  <span class="rating-dim-name">{{ dim.name }}</span>
                </div>
                <div class="rating-buttons">
                  <button
                    v-for="n in 5" :key="n"
                    class="rating-btn"
                    :class="{ selected: ratings[dim.name] === n, past: ratings[dim.name] > n }"
                    :style="ratings[dim.name] >= n ? `--dc:${dim.color}` : ''"
                    @click="ratings[dim.name] = n"
                  >{{ n }}</button>
                </div>
              </div>
            </div>

            <div class="rating-scale-hint">
              <span class="font-mono" style="font-size:0.6rem;color:var(--text-dim);">1 — Not started</span>
              <span class="font-mono" style="font-size:0.6rem;color:var(--text-dim);">5 — Well advanced</span>
            </div>

            <div class="intake-card-footer">
              <button class="btn btn-ghost intake-back" @click="step = 1">← Back</button>
              <button
                class="btn btn-teal"
                style="font-size:0.8rem;padding:0.7rem 1.5rem;"
                :disabled="!ratingsDone"
                @click="step = 3"
              >See my profile →</button>
            </div>
          </div>

          <!-- Step 3: Results -->
          <div class="intake-card results-card" v-else-if="step === 3">
            <div class="intake-card-label font-mono">Your readiness profile</div>

            <div class="results-tier-row">
              <div class="results-tier-badge" :style="`background:${tier.bg};border-color:${tier.color};color:${tier.color}`">
                {{ tier.label }}
              </div>
              <div class="results-score font-mono" :style="`color:${tier.color}`">
                {{ avgScore.toFixed(1) }} <span style="color:var(--text-dim);font-size:0.7em;">/ 5.0</span>
              </div>
            </div>

            <p class="results-insight">{{ tier.desc }}</p>

            <div class="results-sector-note" v-if="profile.sector">
              <svg viewBox="0 0 16 16" fill="none" stroke="#2dd4bf" stroke-width="1.5" style="width:14px;height:14px;flex-shrink:0;margin-top:2px"><circle cx="8" cy="8" r="6"/><line x1="8" y1="7" x2="8" y2="11"/><circle cx="8" cy="5" r=".5" fill="#2dd4bf" stroke="none"/></svg>
              <span>{{ sectorInsight }}</span>
            </div>

            <div class="results-dims">
              <div class="result-dim-row" v-for="dim in dimDefs" :key="dim.name">
                <span class="result-dim-label">{{ dim.name }}</span>
                <div class="result-dim-bar-track">
                  <div class="result-dim-bar-fill" :style="`width:${(ratings[dim.name]/5)*100}%;background:${dim.color}`"></div>
                </div>
                <span class="result-dim-score font-mono" :style="`color:${dim.color}`">{{ ratings[dim.name] }}/5</span>
              </div>
            </div>

            <p class="results-cta-text">
              This profile is a rough self-assessment. IREKAI's full assessment uses expert review,
              technical tooling, and structured interviews to give you a verified, actionable score.
            </p>

            <div class="results-actions">
              <a :href="mailtoLink" class="btn btn-teal" style="font-size:0.8rem;padding:0.75rem 1.6rem;">
                Request your full assessment →
              </a>
              <a href="mailto:info@irekai.nl" class="btn btn-ghost" style="font-size:0.8rem;padding:0.75rem 1.4rem;">
                Just want to talk
              </a>
            </div>

            <button class="intake-restart font-mono" @click="restart">
              ← Start over
            </button>
          </div>

        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed, reactive } from 'vue'

const dialItems = [
  { label: 'Crypto Agility',     score: '2 / 10', color: '#e879f9' },
  { label: 'Asset Inventory',    score: '4 / 10', color: '#22d3ee' },
  { label: 'PQC Availability',   score: '1 / 10', color: '#34d399' },
  { label: 'Governance',         score: '5 / 10', color: '#fbbf24' },
  { label: 'Supplier Management',score: '3 / 10', color: '#a78bfa' },
]

const deliverables = [
  { title: 'Readiness score',           body: 'A single composite score across five cryptographic dimensions — easy to communicate to leadership.' },
  { title: 'Dimension-level breakdown', body: 'Detailed scores for crypto agility, inventory, PQC availability, governance, and supplier management.' },
  { title: 'Risk heat map',             body: 'Visual mapping of your highest-priority vulnerabilities by business impact and urgency.' },
  { title: 'Prioritised action plan',   body: 'A concrete, ordered list of actions with effort estimates and expected risk reduction.' },
  { title: 'Migration roadmap',         body: 'A phased 12–36 month migration roadmap tailored to your organisation\'s size and risk appetite.' },
]

const steps = [
  { title: 'Intake questionnaire',  body: 'A structured set of questions covering your current cryptographic landscape, completed asynchronously.' },
  { title: 'Expert review session', body: 'A 2-hour session with an IREKAI specialist to clarify responses and probe technical depth.' },
  { title: 'Analysis & scoring',    body: 'We score your responses against our maturity model, calibrated to your industry and regulatory context.' },
  { title: 'Results readout',       body: 'A 1-hour readout where we walk through findings, answer questions, and agree on next steps.' },
  { title: 'Report delivery',       body: 'Full written report with all findings, scores, and the prioritised roadmap delivered within 5 business days.' },
]

const areas = [
  { code:'01', name:'Crypto Agility',      color:'#e879f9', desc:'Can you swap algorithms without rewriting systems? We assess abstraction, CI/CD policies, and key rotation capabilities.' },
  { code:'02', name:'Asset Inventory',     color:'#22d3ee', desc:'Do you know what cryptographic assets you have? We evaluate discovery tooling, CBOM practices, and coverage.' },
  { code:'03', name:'PQC Availability',    color:'#34d399', desc:'Are post-quantum algorithms deployed anywhere? We assess library readiness, sandbox testing, and production status.' },
  { code:'04', name:'Governance',          color:'#fbbf24', desc:'Is quantum risk owned and funded? We evaluate executive sponsorship, policy, roadmaps, and compliance alignment.' },
  { code:'05', name:'Supplier Management', color:'#a78bfa', desc:'Are your vendors quantum-ready? We assess supply chain visibility, contract requirements, and SBOM/CBOM coverage.' },
]

// ── Intake questionnaire ─────────────────────────────────────────────────────

const step = ref(0)

const profile = reactive({ sector: null, size: null, driver: null })

const ratings = reactive({
  'Crypto Agility': 0,
  'Asset Inventory': 0,
  'PQC Availability': 0,
  'Governance': 0,
  'Supplier Management': 0,
})

const dimDefs = [
  { name: 'Crypto Agility',      color: '#e879f9' },
  { name: 'Asset Inventory',     color: '#22d3ee' },
  { name: 'PQC Availability',    color: '#34d399' },
  { name: 'Governance',          color: '#fbbf24' },
  { name: 'Supplier Management', color: '#a78bfa' },
]

const sectors = [
  'Finance & Banking',
  'Healthcare & Life Sciences',
  'Government & Defence',
  'Energy & Critical Infrastructure',
  'Technology & Software',
  'Other',
]

const sizes = ['Under 100', '100–999', '1,000–9,999', '10,000+']

const drivers = [
  'IP & data protection',
  'Regulatory compliance',
  'Client / supply chain demand',
  'Board / executive directive',
  'Competitive positioning',
  'Not sure yet',
]

const profileDone = computed(() => profile.sector && profile.size && profile.driver)
const ratingsDone  = computed(() => Object.values(ratings).every(v => v > 0))

const avgScore = computed(() => {
  const vals = Object.values(ratings).filter(v => v > 0)
  if (!vals.length) return 0
  return vals.reduce((a, b) => a + b, 0) / vals.length
})

const tier = computed(() => {
  const s = avgScore.value
  if (s < 1.5) return { label: 'Pre-initial', color: '#f87171', bg: 'rgba(239,68,68,0.08)',   desc: 'Your organisation has not yet meaningfully addressed quantum cryptographic risk. The good news: you\'re early enough to plan properly.' }
  if (s < 2.5) return { label: 'Initial',     color: '#fb923c', bg: 'rgba(249,115,22,0.08)',  desc: 'First steps have been taken, but significant gaps remain across most dimensions. A structured assessment will show where to focus first.' }
  if (s < 3.5) return { label: 'Basic',       color: '#facc15', bg: 'rgba(250,204,21,0.08)',  desc: 'Some areas are progressing, but key dimensions still need structured attention. A roadmap will accelerate your trajectory considerably.' }
  if (s < 4.5) return { label: 'Advanced',    color: '#84cc16', bg: 'rgba(132,204,22,0.08)',  desc: 'Good progress across the board. The focus is shifting to closing gaps and extending readiness to suppliers and dependent systems.' }
  return            { label: 'Managed',       color: '#34d399', bg: 'rgba(52,211,153,0.08)',  desc: 'Strong baseline achieved. Continuous improvement and supplier assurance are the natural next frontier.' }
})

const sectorInsight = computed(() => {
  const map = {
    'Finance & Banking':               'DORA enforcement makes cryptographic agility a regulated requirement — your migration clock is already running.',
    'Healthcare & Life Sciences':       'Patient data retention periods mean harvest-now-decrypt-later attacks pose a real, long-term confidentiality risk to your records.',
    'Government & Defence':            'CNSA 2.0 sets firm migration deadlines. Classified and sensitive workloads need quantum-safe transport now.',
    'Energy & Critical Infrastructure': 'NIS2 critical entity requirements put cryptographic resilience front and centre for operational continuity.',
    'Technology & Software':           'Your clients\' security postures depend on your cryptographic readiness — supplier assessment requests are already incoming.',
    'Other':                           'Regardless of sector, harvest-now-decrypt-later attacks mean data you protect today could be exposed in a few years.',
  }
  return map[profile.sector] || ''
})

const mailtoLink = computed(() => {
  const subject = encodeURIComponent(
    `Quantum Readiness Profile – ${profile.sector || 'Organisation'} – ${profile.size || 'Unknown size'}`
  )
  const body = encodeURIComponent(
    `Hi IREKAI team,\n\nI completed the quick readiness profile on your website. Here are my results:\n\n` +
    `Organisation profile\n` +
    `  Sector: ${profile.sector}\n` +
    `  Size: ${profile.size}\n` +
    `  Primary compliance driver: ${profile.driver}\n\n` +
    `Dimension self-ratings (1 = not started, 5 = well advanced)\n` +
    Object.entries(ratings).map(([k, v]) => `  ${k}: ${v}/5`).join('\n') + '\n\n' +
    `Estimated maturity tier: ${tier.value.label} (avg ${avgScore.value.toFixed(1)}/5)\n\n` +
    `I'd like to discuss a full Quantum Readiness Assessment. Please get in touch.\n\nKind regards`
  )
  return `mailto:info@irekai.nl?subject=${subject}&body=${body}`
})

function restart() {
  step.value = 0
  profile.sector = null
  profile.size   = null
  profile.driver = null
  Object.keys(ratings).forEach(k => { ratings[k] = 0 })
}
</script>

<style scoped>
.hero-top { display: flex; align-items: center; justify-content: space-between; margin-bottom: 2.5rem; flex-wrap: wrap; gap: 1rem; }
.breadcrumb { font-family: var(--font-mono); font-size: 0.72rem; color: var(--text-dim); text-decoration: none; transition: color 0.15s; }
.breadcrumb:hover { color: var(--text-muted); }

.hero-body { display: grid; grid-template-columns: 1fr; gap: 3rem; align-items: center; }
@media (min-width: 900px) { .hero-body { grid-template-columns: 1fr 380px; } }

.hero-h1 { font-size: clamp(2rem, 5vw, 3.2rem); font-weight: 500; line-height: 1.15; color: var(--text); margin-bottom: 1.25rem; }
.hero-lead { font-size: 1rem; line-height: 1.75; color: var(--text-muted); max-width: 56ch; margin-bottom: 2rem; }
.hero-actions { display: flex; flex-wrap: wrap; gap: 0.75rem; }

/* Dial card */
.readiness-dial-card { background: rgba(28,25,23,0.7); border: 1px solid var(--border); border-radius: 14px; padding: 1.75rem; }
.dial-label { font-family: var(--font-mono); font-size: 0.62rem; letter-spacing: 0.18em; text-transform: uppercase; color: var(--text-dim); margin-bottom: 1rem; }
.dial-rings { display: flex; justify-content: center; margin-bottom: 1.5rem; }
.dial-rings svg { width: 120px; height: 120px; }
.dial-legend { display: flex; flex-direction: column; gap: 0.55rem; }
.dial-legend-row { display: flex; align-items: center; gap: 0.6rem; }
.dial-dot { width: 6px; height: 6px; border-radius: 50%; flex-shrink: 0; }
.dial-name { font-family: var(--font-mono); font-size: 0.68rem; color: var(--text-muted); flex: 1; }
.dial-score { font-family: var(--font-mono); font-size: 0.68rem; font-weight: 600; }

/* Content sections */
.content-section { padding: 4rem 0; border-top: 1px solid var(--border); }
.two-col { display: grid; grid-template-columns: 1fr; gap: 3rem; }
@media (min-width: 768px) { .two-col { grid-template-columns: 1fr 1fr; } }

.deliverable-list { display: flex; flex-direction: column; gap: 1.25rem; }
.deliverable { display: flex; gap: 0.75rem; align-items: flex-start; }
.deliverable-icon { width: 20px; height: 20px; flex-shrink: 0; margin-top: 0.15rem; }
.deliverable-icon svg { width: 100%; height: 100%; }
.deliverable-title { font-size: 0.9rem; font-weight: 500; color: var(--text); margin-bottom: 0.25rem; }
.deliverable-body { font-size: 0.82rem; line-height: 1.6; color: var(--text-muted); }

.steps { display: flex; flex-direction: column; gap: 1.25rem; }
.step { display: flex; gap: 1rem; align-items: flex-start; }
.step-num { font-family: var(--font-mono); font-size: 0.65rem; color: #2dd4bf; opacity: 0.7; min-width: 1.8rem; padding-top: 0.15rem; }
.step-title { font-size: 0.9rem; font-weight: 500; color: var(--text); margin-bottom: 0.25rem; }
.step-body { font-size: 0.82rem; line-height: 1.6; color: var(--text-muted); }

/* Areas */
.areas-section { padding: 4rem 0; border-top: 1px solid var(--border); }
.areas-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 1rem; }
.area-card { padding: 1.25rem; border-radius: 10px; border: 1px solid rgba(255,255,255,0.06); background: rgba(28,25,23,0.5); transition: border-color 0.2s; }
.area-card:hover { border-color: var(--c); }
.area-code { font-size: 0.6rem; letter-spacing: 0.2em; color: var(--c); margin-bottom: 0.5rem; }
.area-name { font-size: 0.95rem; color: var(--text); margin-bottom: 0.5rem; }
.area-desc { font-size: 0.78rem; line-height: 1.6; color: var(--text-muted); }

/* ── Intake section ──────────────────────────────────────────── */
.intake-section { padding: 3rem 0 5rem; border-top: 1px solid var(--border); }

/* Intro state */
.intake-intro { max-width: 560px; }
.intake-heading { font-size: clamp(1.5rem, 3.5vw, 2rem); font-weight: 500; line-height: 1.2; color: var(--text); margin-bottom: 1rem; }
.intake-lead { font-size: 0.9rem; line-height: 1.75; color: var(--text-muted); margin-bottom: 2rem; max-width: 52ch; }
.intake-start-btn { font-size: 0.8rem; padding: 0.8rem 1.75rem; }

/* Progress */
.intake-flow { max-width: 680px; }
.intake-progress { display: flex; align-items: center; gap: 0; margin-bottom: 2.5rem; }
.progress-step { display: flex; flex-direction: column; align-items: center; gap: 0.4rem; }
.progress-dot {
  width: 28px; height: 28px;
  border-radius: 50%;
  border: 1px solid var(--border);
  display: flex; align-items: center; justify-content: center;
  font-family: var(--font-mono); font-size: 0.65rem;
  color: var(--text-dim);
  transition: all 0.2s;
}
.progress-step.active .progress-dot { border-color: #2dd4bf; color: #2dd4bf; background: rgba(45,212,191,0.08); }
.progress-step.done .progress-dot { border-color: #2dd4bf; color: #2dd4bf; background: rgba(45,212,191,0.12); }
.progress-label { font-family: var(--font-mono); font-size: 0.58rem; letter-spacing: 0.12em; text-transform: uppercase; color: var(--text-dim); }
.progress-step.active .progress-label, .progress-step.done .progress-label { color: var(--text-muted); }
.progress-line { flex: 1; height: 1px; background: var(--border); margin: 0 0.5rem; margin-bottom: 1.1rem; transition: background 0.3s; }
.progress-line.active { background: rgba(45,212,191,0.4); }

/* Card */
.intake-card {
  background: rgba(28,25,23,0.7);
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 2rem 2.25rem;
}
.intake-card-label { font-size: 0.6rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--text-dim); margin-bottom: 0.75rem; }
.intake-card-heading { font-size: 1.2rem; font-weight: 500; color: var(--text); margin-bottom: 1.75rem; }

/* Fields */
.intake-field { margin-bottom: 1.5rem; }
.intake-field-label { font-family: var(--font-mono); font-size: 0.68rem; letter-spacing: 0.08em; color: var(--text-muted); margin-bottom: 0.6rem; }

/* Pill selectors */
.pill-group { display: flex; flex-wrap: wrap; gap: 0.5rem; }
.pill {
  font-family: var(--font-mono);
  font-size: 0.7rem;
  padding: 0.4rem 0.85rem;
  border-radius: 6px;
  border: 1px solid var(--border);
  background: transparent;
  color: var(--text-muted);
  cursor: pointer;
  transition: all 0.15s;
}
.pill:hover { border-color: rgba(45,212,191,0.4); color: var(--text); }
.pill.selected { border-color: #2dd4bf; background: rgba(45,212,191,0.1); color: #2dd4bf; }

/* Footer */
.intake-card-footer { display: flex; align-items: center; justify-content: space-between; margin-top: 2rem; }
.intake-back { font-size: 0.75rem; padding: 0.5rem 0.75rem; opacity: 0.7; }
.intake-back:hover { opacity: 1; }
.btn[disabled] { opacity: 0.35; cursor: not-allowed; pointer-events: none; }

/* Self-rating step */
.intake-subtext { font-size: 0.82rem; color: var(--text-dim); margin-bottom: 1.5rem; margin-top: -0.75rem; }
.ratings-list { display: flex; flex-direction: column; gap: 1rem; }
.rating-row { display: flex; align-items: center; justify-content: space-between; gap: 1rem; flex-wrap: wrap; }
.rating-row-left { display: flex; align-items: center; gap: 0.6rem; min-width: 160px; }
.rating-dim-dot { width: 7px; height: 7px; border-radius: 50%; flex-shrink: 0; }
.rating-dim-name { font-size: 0.82rem; color: var(--text-muted); }
.rating-buttons { display: flex; gap: 0.35rem; }
.rating-btn {
  width: 32px; height: 32px;
  border-radius: 6px;
  border: 1px solid var(--border);
  background: transparent;
  font-family: var(--font-mono);
  font-size: 0.7rem;
  color: var(--text-dim);
  cursor: pointer;
  transition: all 0.15s;
}
.rating-btn:hover { border-color: rgba(255,255,255,0.2); color: var(--text); }
.rating-btn.past { border-color: var(--dc, rgba(45,212,191,0.3)); background: rgba(45,212,191,0.05); color: var(--text-dim); }
.rating-btn.selected { border-color: var(--dc, #2dd4bf); background: var(--dc, #2dd4bf); color: #0c0a09; font-weight: 600; }
.rating-scale-hint { display: flex; justify-content: space-between; margin-top: 1rem; padding: 0 0.5rem; }

/* Results card */
.results-card { border-color: rgba(45,212,191,0.2); }
.results-tier-row { display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem; }
.results-tier-badge {
  font-family: var(--font-mono);
  font-size: 0.68rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  padding: 0.3rem 0.7rem;
  border-radius: 5px;
  border: 1px solid;
}
.results-score { font-size: 1.4rem; font-weight: 600; }
.results-insight { font-size: 0.875rem; line-height: 1.7; color: var(--text-muted); margin-bottom: 1rem; }
.results-sector-note {
  display: flex; align-items: flex-start; gap: 0.6rem;
  font-size: 0.8rem; line-height: 1.6; color: var(--text-muted);
  background: rgba(45,212,191,0.05);
  border: 1px solid rgba(45,212,191,0.15);
  border-radius: 8px;
  padding: 0.75rem 1rem;
  margin-bottom: 1.5rem;
}

.results-dims { display: flex; flex-direction: column; gap: 0.65rem; margin-bottom: 1.5rem; }
.result-dim-row { display: flex; align-items: center; gap: 0.75rem; }
.result-dim-label { font-family: var(--font-mono); font-size: 0.65rem; color: var(--text-dim); width: 140px; flex-shrink: 0; }
.result-dim-bar-track { flex: 1; height: 4px; background: rgba(255,255,255,0.06); border-radius: 2px; overflow: hidden; }
.result-dim-bar-fill { height: 100%; border-radius: 2px; transition: width 0.6s ease; }
.result-dim-score { font-family: var(--font-mono); font-size: 0.65rem; width: 2.5rem; text-align: right; flex-shrink: 0; }

.results-cta-text { font-size: 0.78rem; line-height: 1.7; color: var(--text-dim); margin-bottom: 1.5rem; border-top: 1px solid var(--border); padding-top: 1.25rem; }
.results-actions { display: flex; flex-wrap: wrap; gap: 0.75rem; margin-bottom: 1.5rem; }

.intake-restart {
  background: none; border: none; cursor: pointer;
  font-size: 0.65rem; letter-spacing: 0.1em; color: var(--text-dim);
  padding: 0; transition: color 0.15s;
}
.intake-restart:hover { color: var(--text-muted); }

/* btn-teal local fallback */
.btn-teal {
  display: inline-flex; align-items: center; gap: 0.5rem;
  font-family: var(--font-mono); font-size: 0.72rem;
  padding: 0.38rem 0.9rem; border-radius: 6px;
  border: 1px solid rgba(45,212,191,0.4);
  background: rgba(45,212,191,0.1); color: #2dd4bf;
  transition: all 0.2s; text-decoration: none; cursor: pointer;
}
.btn-teal:hover {
  background: rgba(45,212,191,0.18); border-color: rgba(45,212,191,0.7);
  box-shadow: 0 0 18px -5px rgba(45,212,191,0.4);
}
</style>
