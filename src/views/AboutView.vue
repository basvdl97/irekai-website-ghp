<template>
  <div>
    <section class="product-hero">
      <div class="container">
        <div class="hero-top">
          <RouterLink to="/" class="breadcrumb">← Back to home</RouterLink>
        </div>

        <div class="about-hero-body">
          <!-- Left: intro text -->
          <div>
            <div class="section-label" style="margin-bottom:1rem;">About IREKAI</div>
            <h1 class="font-display" style="font-size:clamp(2rem,5vw,3.2rem);font-weight:500;line-height:1.15;color:var(--text);margin-bottom:1.25rem;">
              Helping organisations<br/>
              <em style="color:#7aad97">navigate the quantum transition.</em>
            </h1>
            <div class="prose" style="color:var(--text-muted);">
              <p>
                IREKAI is a post-quantum cryptography consultancy and tooling provider. We work with
                organisations of all sizes — from scale-ups to critical infrastructure operators —
                to assess, plan, and execute their migration to quantum-safe cryptography.
              </p>
              <p>
                Quantum computing is not a distant threat. The harvest-now-decrypt-later (HNDL) attack
                vector means your encrypted data is at risk today, even if cryptographically-relevant
                quantum computers are still years away. In addition, a full migration is estimated to take 5–10 years. IREKAI helps you act now, pragmatically.
              </p>
              <p>
                We combine deep cryptographic expertise with practical engineering. Our
                frameworks are grounded in NIST FIPS 203/204/205, BSI, ANSSI, and EU regulatory
                requirements — and are kept refined through real migration engagements.
              </p>
            </div>
          </div>

          <!-- Right: name etymology — static final frame of the animation -->
          <div class="etymology-card">
            <!-- Two source words -->
            <div class="etym-sources">
              <div class="etym-word">
                <span class="etym-glyph">ἠρεμία</span>
                <span class="etym-roman">IREMIA</span>
                <span class="etym-label">Greek · peace of mind</span>
              </div>
              <div class="etym-divider"></div>
              <div class="etym-word">
                <span class="etym-glyph">意気概</span>
                <span class="etym-roman">IKIGAI</span>
                <span class="etym-label">Japanese · purpose</span>
              </div>
            </div>

            <!-- Arrow -->
            <div class="etym-arrow-wrap">
              <svg class="etym-arrow" viewBox="0 0 24 32" fill="none" stroke="#7aad97" stroke-width="1" stroke-opacity=".4">
                <line x1="12" y1="0" x2="12" y2="28"/>
                <path d="M6 22l6 8 6-8"/>
              </svg>
            </div>

            <!-- IREKAI result -->
            <div class="etym-result">
              <div class="etym-seal-wrap">
                <svg viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <defs>
                    <pattern id="ab2-lat" x="0" y="0" width="12" height="12"
                             patternUnits="userSpaceOnUse" patternTransform="rotate(45 100 100)">
                      <circle cx="0" cy="0" r="1.3" fill="#7aad97" fill-opacity=".55"/>
                    </pattern>
                    <clipPath id="ab2-clip">
                      <rect x="69" y="69" width="62" height="62"/>
                    </clipPath>
                  </defs>
                  <rect x="28" y="28" width="144" height="144" fill="none" stroke="#7aad97" stroke-width="1.6"/>
                  <g stroke="#7aad97" stroke-width="1.1" stroke-opacity=".65" stroke-linecap="square">
                    <line x1="17" y1="28" x2="28" y2="28"/><line x1="28" y1="17" x2="28" y2="28"/>
                    <line x1="172" y1="28" x2="183" y2="28"/><line x1="172" y1="17" x2="172" y2="28"/>
                    <line x1="172" y1="172" x2="183" y2="172"/><line x1="172" y1="172" x2="172" y2="183"/>
                    <line x1="17" y1="172" x2="28" y2="172"/><line x1="28" y1="172" x2="28" y2="183"/>
                  </g>
                  <rect x="69" y="69" width="62" height="62" fill="url(#ab2-lat)" clip-path="url(#ab2-clip)"/>
                  <rect x="68" y="68" width="64" height="64" fill="none" stroke="#7aad97" stroke-width=".9" stroke-opacity=".42"/>
                  <g stroke="#7aad97" stroke-opacity=".22" stroke-width=".7">
                    <line x1="100" y1="68" x2="100" y2="132"/>
                    <line x1="68" y1="100" x2="132" y2="100"/>
                  </g>
                  <circle cx="100" cy="100" r="6.5" fill="none" stroke="#7aad97" stroke-width="1.1" stroke-opacity=".74"/>
                  <circle cx="100" cy="100" r="2.7" fill="#7aad97"/>
                </svg>
              </div>
              <div class="etym-name">IREKAI</div>
              <div class="etym-tagline">Clarity first. Migrate with confidence.</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Mission -->
    <section class="mission-section">
      <div class="container">
        <div class="mission-grid">
          <div class="mission-item" v-for="m in mission" :key="m.title">
            <div class="mission-icon" v-html="m.icon"></div>
            <div class="mission-title font-display">{{ m.title }}</div>
            <div class="mission-body">{{ m.body }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Standards alignment -->
    <section class="standards-section">
      <div class="container">
        <div class="section-label" style="margin-bottom:1.25rem;">Standards &amp; frameworks alignment</div>
        <div class="standards-grid">
          <div class="standard-card" v-for="s in standards" :key="s.name">
            <div class="std-name font-mono">{{ s.name }}</div>
            <div class="std-body">{{ s.body }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact -->
    <section class="contact-section">
      <div class="container">
        <div class="contact-card">
          <div>
            <h3 class="font-display" style="font-size:1.5rem;margin-bottom:0.6rem;">Get in touch</h3>
            <p class="prose" style="max-width:48ch;">
              Whether you're taking your first steps or mid-migration, we're happy to discuss your
              specific situation and how IREKAI can help.
            </p>
          </div>
          <div class="contact-actions">
            <a href="mailto:info@irekai.nl" class="btn btn-sage" style="font-size:0.8rem;padding:0.75rem 1.5rem;">
              info@irekai.nl →
            </a>
            <a href="https://irekai.nl" target="_blank" rel="noopener" class="btn btn-ghost" style="font-size:0.8rem;padding:0.75rem 1.5rem;">
              irekai.nl ↗
            </a>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const mission = [
  {
    title: 'Expert-led',
    body: 'Our team combines academic cryptographic research with hands-on migration experience across multiple domains.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>`
  },
  {
    title: 'Compliancy-first',
    body: 'Every IREKAI engagement produces tangible compliance evidence. Demonstrate your quantum-readiness posture to auditors, regulators, and clients — aligned with NIS2, DORA, ISO 27001, and CNSA 2.0.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/><polyline points="9 12 11 14 15 10"/></svg>`
  },
  {
    title: 'Practical focus',
    body: 'We don\'t produce shelf reports. Every IREKAI engagement ends with tools, templates, and a concrete plan your team can execute — without a permanent consulting retainer.',
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>`
  },
]

const standards = [
  { name: 'NIST FIPS 203/204/205', body: 'ML-KEM, ML-DSA, SLH-DSA — the standardised post-quantum algorithms our work is built on.' },
  { name: 'CNSA 2.0',              body: 'US National Security Systems Committee algorithm requirements and timelines.' },
  { name: 'BSI TR-02102',          body: 'German Federal Office for Information Security cryptographic guidelines.' },
  { name: 'ANSSI',                 body: 'French cybersecurity agency recommendations for PQC migration.' },
  { name: 'ETSI / ISO',            body: 'European and international standardisation body guidance on quantum-safe cryptography.' },
  { name: 'EU NIS2 / DORA',        body: 'EU regulatory requirements for cybersecurity risk management, including cryptographic controls.' },
  { name: 'ISO 27001',             body: 'Annex A cryptographic controls and evidence requirements for compliance.' },
  { name: 'CycloneDX CBOM',        body: 'Cryptographic Bill of Materials standard for machine-readable crypto asset inventory.' },
]
</script>

<style scoped>
.hero-top { margin-bottom: 2.5rem; }
.breadcrumb { font-family: var(--font-mono); font-size: 0.72rem; color: var(--text-dim); text-decoration: none; transition: color 0.15s; }
.breadcrumb:hover { color: var(--text-muted); }

.about-hero-body {
  display: grid;
  grid-template-columns: 1fr;
  gap: 3rem;
  align-items: center;
}
@media (min-width: 900px) { .about-hero-body { grid-template-columns: 1fr auto; } }

/* ── Etymology card ─────────────────────────────────────────── */
.etymology-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0;
  padding: 2rem 2.5rem 1.75rem;
  border: 1px solid var(--border);
  border-radius: 14px;
  background: rgba(28,25,23,0.5);
  min-width: 240px;
}

.etym-sources {
  display: flex;
  align-items: flex-start;
  gap: 1.25rem;
  width: 100%;
  justify-content: center;
}

.etym-word {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.35rem;
}

.etym-glyph {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(1.1rem, 2.5vw, 1.4rem);
  font-weight: 400;
  color: #7aad97;
  opacity: 0.85;
  letter-spacing: 0.02em;
}

.etym-roman {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(0.75rem, 1.5vw, 0.9rem);
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.etym-label {
  font-family: var(--font-mono);
  font-size: 0.6rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--text-dim);
  text-align: center;
  line-height: 1.5;
}

.etym-divider {
  width: 1px;
  height: 3rem;
  background: var(--border);
  margin-top: 0.5rem;
  opacity: 0.6;
}

.etym-arrow-wrap {
  margin: 0.75rem 0;
}
.etym-arrow {
  width: 16px;
  height: 22px;
  opacity: 0.5;
}

.etym-result {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.6rem;
}

.etym-seal-wrap {
  width: clamp(56px, 10vw, 72px);
  height: clamp(56px, 10vw, 72px);
  filter: drop-shadow(0 0 14px rgba(122,173,151,0.3));
}
.etym-seal-wrap svg { width: 100%; height: 100%; }

.etym-name {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(1.5rem, 3.5vw, 2rem);
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--text);
}

.etym-tagline {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-style: italic;
  font-size: 0.82rem;
  color: var(--text-dim);
  letter-spacing: 0.02em;
  text-align: center;
}

/* ── Mission ─────────────────────────────────────────────────── */
.mission-section { padding: 4rem 0; border-top: 1px solid var(--border); }
.mission-grid { display: grid; grid-template-columns: 1fr; gap: 2.5rem; }
@media (min-width: 640px) { .mission-grid { grid-template-columns: repeat(3, 1fr); } }

.mission-item { display: flex; flex-direction: column; gap: 1rem; }
.mission-icon { width: 32px; height: 32px; color: #7aad97; opacity: 0.8; }
.mission-icon svg { width: 100%; height: 100%; }
.mission-title { font-size: 1.05rem; color: var(--text); }
.mission-body { font-size: 0.85rem; line-height: 1.75; color: var(--text-muted); }

/* ── Standards ────────────────────────────────────────────────── */
.standards-section { padding: 4rem 0; border-top: 1px solid var(--border); }
.standards-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 1rem; }
.standard-card {
  padding: 1.1rem 1.25rem;
  border-radius: 10px;
  border: 1px solid var(--border);
  background: rgba(28,25,23,0.5);
  transition: border-color 0.2s;
}
.standard-card:hover { border-color: rgba(122,173,151,0.35); }
.std-name { font-size: 0.7rem; letter-spacing: 0.08em; color: #7aad97; margin-bottom: 0.5rem; opacity: 0.9; }
.std-body { font-size: 0.78rem; line-height: 1.6; color: var(--text-muted); }

/* ── Contact ──────────────────────────────────────────────────── */
.contact-section { padding: 3rem 0 5rem; }
.contact-card {
  background: rgba(122,173,151,0.06);
  border: 1px solid rgba(122,173,151,0.2);
  border-radius: 14px;
  padding: 2.5rem;
  display: flex;
  flex-direction: column;
  gap: 2rem;
  align-items: flex-start;
}
@media (min-width: 640px) {
  .contact-card { flex-direction: row; align-items: center; justify-content: space-between; }
}
.contact-actions { display: flex; gap: 0.75rem; flex-wrap: wrap; flex-shrink: 0; }

/* btn-sage (local fallback) */
.btn-sage {
  display: inline-flex; align-items: center; gap: 0.5rem;
  font-family: var(--font-mono); font-size: 0.72rem; padding: 0.38rem 0.9rem;
  border-radius: 6px; border: 1px solid rgba(122,173,151,0.4);
  background: rgba(122,173,151,0.1); color: #7aad97;
  transition: all 0.2s; text-decoration: none;
}
.btn-sage:hover {
  background: rgba(122,173,151,0.18); border-color: rgba(122,173,151,0.7);
  box-shadow: 0 0 18px -5px rgba(122,173,151,0.4);
}
</style>
