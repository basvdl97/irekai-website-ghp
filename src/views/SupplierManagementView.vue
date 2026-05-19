<template>
  <div>
    <section class="product-hero">
      <div class="container">
        <div class="hero-top">
          <RouterLink to="/" class="breadcrumb">← Back to home</RouterLink>
          <span class="badge" style="background:rgba(167,139,250,0.1);color:#a78bfa;border-color:rgba(167,139,250,0.35);">
            Programme
          </span>
        </div>

        <div class="hero-body">
          <div class="hero-text">
            <div class="section-label" style="margin-bottom:1rem;color:#a78bfa;opacity:0.85;">
              03 · Quantum Threat Supplier Management Programme
            </div>
            <h1 class="hero-h1 font-display">
              Your perimeter ends<br/>
              <em style="color:#a78bfa">where your vendors begin.</em>
            </h1>
            <p class="hero-lead">
              Third-party cryptographic risk is one of the most underestimated exposure surfaces in
              the quantum transition. IREKAI's Supplier Management Programme gives you structured
              tools, templates, and processes to extend quantum-readiness across your entire supply chain.
            </p>
            <div class="hero-actions">
              <a href="mailto:info@irekai.nl?subject=Supplier Management Programme" class="btn" style="background:rgba(167,139,250,0.1);border-color:rgba(167,139,250,0.4);color:#a78bfa;font-size:0.8rem;padding:0.75rem 1.6rem;">
                Request programme →
              </a>
              <a href="mailto:info@irekai.nl" class="btn btn-ghost" style="font-size:0.8rem;padding:0.75rem 1.5rem;">
                Learn more
              </a>
            </div>
          </div>

          <!-- Supply chain visual -->
          <div class="supply-card">
            <div class="font-mono" style="font-size:0.62rem;letter-spacing:0.18em;text-transform:uppercase;color:var(--text-dim);margin-bottom:1.25rem;">
              Supply chain risk tiers
            </div>
            <div class="supply-tiers">
              <div class="supply-tier" v-for="t in supplyTiers" :key="t.label">
                <div class="supply-bar" :style="`width:${t.fill}%;background:${t.color}`"></div>
                <div class="supply-info">
                  <span class="supply-label">{{ t.label }}</span>
                  <span class="supply-pct font-mono" :style="`color:${t.color}`">{{ t.risk }}</span>
                </div>
              </div>
            </div>
            <div class="supply-note">
              Risk exposure across vendor categories before implementation of the programme.
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Programme phases -->
    <section class="phases-section">
      <div class="container">
        <div class="section-label" style="margin-bottom:1.5rem;">Programme phases</div>
        <div class="phases-grid">
          <div class="phase-card" v-for="p in phases" :key="p.phase">
            <div class="phase-num font-mono">Phase {{ p.phase }}</div>
            <div class="phase-name font-display">{{ p.name }}</div>
            <div class="phase-desc">{{ p.desc }}</div>
            <ul class="phase-items">
              <li v-for="item in p.items" :key="item">{{ item }}</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- What's included -->
    <section class="included-section">
      <div class="container">
        <div class="two-col">
          <div>
            <div class="section-label" style="margin-bottom:1.25rem;">What's included</div>
            <div class="included-list">
              <div class="included-item" v-for="item in included" :key="item.title">
                <div class="included-icon" v-html="item.icon"></div>
                <div>
                  <div class="included-title">{{ item.title }}</div>
                  <div class="included-body">{{ item.body }}</div>
                </div>
              </div>
            </div>
          </div>
          <div>
            <div class="section-label" style="margin-bottom:1.25rem;">Key outcomes</div>
            <div class="outcomes">
              <div class="outcome" v-for="o in outcomes" :key="o">
                <div class="outcome-check">✓</div>
                <span>{{ o }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Teaser download -->
    <section class="teaser-download">
      <div class="container">
        <div class="dl-card">
          <div class="badge violet-badge" style="margin-bottom:0.75rem;">Preview available</div>
          <h3 class="font-display" style="font-size:1.3rem;margin-bottom:0.6rem;">
            Programme overview — teaser
          </h3>
          <p class="prose" style="margin-bottom:1.5rem;">
            Read a high-level overview of the Quantum Threat Supplier Management Programme,
            including the assessment framework and sample deliverables.
          </p>
          <a href="mailto:info@irekai.nl?subject=Supplier Management Teaser" class="btn" style="background:rgba(167,139,250,0.1);border-color:rgba(167,139,250,0.4);color:#a78bfa;font-size:0.8rem;">
            Request teaser document →
          </a>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const supplyTiers = [
  { label: 'Tier 1 — Critical software vendors', fill: 92, color: '#f87171', risk: 'Critical' },
  { label: 'Tier 2 — Hardware & HSM suppliers',  fill: 75, color: '#fb923c', risk: 'High' },
  { label: 'Tier 3 — SaaS & cloud services',     fill: 68, color: '#fbbf24', risk: 'High' },
  { label: 'Tier 4 — OT / IoT suppliers',        fill: 55, color: '#fbbf24', risk: 'Medium' },
  { label: 'Tier 5 — Long-tail vendors',          fill: 40, color: '#a3e635', risk: 'Medium' },
]

const phases = [
  {
    phase: 1, name: 'Discovery & Scoping',
    desc: 'Identify and classify all third-party cryptographic dependencies.',
    items: ['Critical vendor catalogue', 'SBOM/CBOM intake', 'Dependency risk tier assignment']
  },
  {
    phase: 2, name: 'Assessment',
    desc: 'Structured questionnaires and workshops to evaluate vendor posture.',
    items: ['Vendor crypto questionnaire', 'Workshop facilitation', 'PQC roadmap documentation']
  },
  {
    phase: 3, name: 'Requirements & Contracting',
    desc: 'Embed quantum-readiness into procurement and existing agreements.',
    items: ['Contract language templates', 'PQC procurement clauses', 'Remediation timelines']
  },
  {
    phase: 4, name: 'Monitoring & Assurance',
    desc: 'Ongoing visibility into supplier quantum posture.',
    items: ['Supplier migration tracker', 'Continuous CBOM monitoring', 'Escalation process']
  },
]

const included = [
  {
    title: 'Vendor assessment questionnaire',
    body: 'A structured, weighted questionnaire to evaluate any vendor\'s current cryptographic posture and PQC readiness.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/></svg>`
  },
  {
    title: 'Risk scoring methodology',
    body: 'Quantitative risk scoring framework that integrates vendor scores into your overall cryptographic risk register.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M18 20V10M12 20V4M6 20v-6"/></svg>`
  },
  {
    title: 'Contract clause library',
    body: 'Ready-to-use contract language covering PQC migration milestones, SBOM/CBOM disclosure, and audit rights.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>`
  },
  {
    title: 'Migration tracker template',
    body: 'A structured tracking sheet for monitoring vendor PQC migration commitments and progress over time.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>`
  },
]

const outcomes = [
  'Full visibility into third-party cryptographic exposure',
  'PQC requirements embedded in all new and renewed contracts',
  'Prioritised vendor remediation roadmap',
  'Continuous SBOM/CBOM-driven monitoring in place',
  'Audit-ready evidence of supply chain quantum governance',
  'Escalation process for non-compliant vendors',
]
</script>

<style scoped>
.hero-top { display: flex; align-items: center; justify-content: space-between; margin-bottom: 2.5rem; flex-wrap: wrap; gap: 1rem; }
.breadcrumb { font-family: var(--font-mono); font-size: 0.72rem; color: var(--text-dim); text-decoration: none; transition: color 0.15s; }
.breadcrumb:hover { color: var(--text-muted); }

.hero-body { display: grid; grid-template-columns: 1fr; gap: 3rem; align-items: flex-start; }
@media (min-width: 900px) { .hero-body { grid-template-columns: 1fr 380px; } }

.hero-h1 { font-size: clamp(1.9rem, 5vw, 3rem); font-weight: 500; line-height: 1.15; color: var(--text); margin-bottom: 1.25rem; }
.hero-lead { font-size: 1rem; line-height: 1.75; color: var(--text-muted); max-width: 56ch; margin-bottom: 2rem; }
.hero-actions { display: flex; flex-wrap: wrap; gap: 0.75rem; }

/* Supply card */
.supply-card {
  background: rgba(28,25,23,0.7);
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 1.5rem;
}
.supply-tiers { display: flex; flex-direction: column; gap: 0.85rem; margin-bottom: 1rem; }
.supply-tier { display: flex; flex-direction: column; gap: 0.3rem; }
.supply-bar { height: 3px; border-radius: 2px; transition: width 1s ease; }
.supply-info { display: flex; justify-content: space-between; align-items: center; }
.supply-label { font-family: var(--font-mono); font-size: 0.65rem; color: var(--text-muted); }
.supply-pct { font-size: 0.65rem; font-weight: 600; }
.supply-note { font-family: var(--font-mono); font-size: 0.6rem; color: var(--text-dim); line-height: 1.5; border-top: 1px solid var(--border); padding-top: 0.75rem; }

/* Phases */
.phases-section { padding: 4rem 0; border-top: 1px solid var(--border); }
.phases-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 1rem; }
.phase-card {
  padding: 1.4rem;
  border-radius: 12px;
  border: 1px solid rgba(167,139,250,0.2);
  background: rgba(167,139,250,0.04);
}
.phase-num { font-size: 0.6rem; letter-spacing: 0.2em; color: #a78bfa; margin-bottom: 0.5rem; }
.phase-name { font-size: 0.95rem; color: var(--text); margin-bottom: 0.5rem; }
.phase-desc { font-size: 0.78rem; line-height: 1.6; color: var(--text-muted); margin-bottom: 0.75rem; }
.phase-items { list-style: none; display: flex; flex-direction: column; gap: 0.35rem; padding: 0; }
.phase-items li {
  font-family: var(--font-mono);
  font-size: 0.65rem;
  color: var(--text-dim);
  padding-left: 1rem;
  position: relative;
}
.phase-items li::before { content: '·'; position: absolute; left: 0; color: #a78bfa; }

/* Included */
.included-section { padding: 4rem 0; border-top: 1px solid var(--border); }
.two-col { display: grid; grid-template-columns: 1fr; gap: 3rem; }
@media (min-width: 768px) { .two-col { grid-template-columns: 1fr 1fr; } }

.included-list { display: flex; flex-direction: column; gap: 1.5rem; }
.included-item { display: flex; gap: 0.85rem; align-items: flex-start; }
.included-icon { width: 20px; height: 20px; color: #a78bfa; flex-shrink: 0; margin-top: 0.1rem; }
.included-icon svg { width: 100%; height: 100%; }
.included-title { font-size: 0.9rem; font-weight: 500; color: var(--text); margin-bottom: 0.25rem; }
.included-body { font-size: 0.82rem; line-height: 1.6; color: var(--text-muted); }

.outcomes { display: flex; flex-direction: column; gap: 0.8rem; }
.outcome {
  display: flex;
  align-items: flex-start;
  gap: 0.65rem;
  font-size: 0.875rem;
  line-height: 1.6;
  color: var(--text-muted);
}
.outcome-check { color: #a78bfa; font-size: 0.85rem; flex-shrink: 0; margin-top: 0.1rem; }

/* Teaser download */
.teaser-download { padding: 3rem 0 5rem; }
.dl-card {
  background: rgba(167,139,250,0.04);
  border: 1px solid rgba(167,139,250,0.2);
  border-radius: 14px;
  padding: 2.5rem;
  max-width: 600px;
}
.violet-badge { background: rgba(167,139,250,0.1); color: #a78bfa; border-color: rgba(167,139,250,0.3); }
</style>
