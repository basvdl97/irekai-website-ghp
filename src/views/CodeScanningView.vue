<template>
  <div>
    <section class="product-hero">
      <div class="container">
        <div class="hero-top">
          <RouterLink to="/" class="breadcrumb">← Back to home</RouterLink>
          <span class="badge" style="background:rgba(232,121,249,0.1);color:#e879f9;border-color:rgba(232,121,249,0.35);">
            Coming soon
          </span>
        </div>

        <div class="hero-body">
          <div class="hero-text">
            <div class="section-label" style="margin-bottom:1rem;color:#e879f9;opacity:0.85;">
              04 · Cryptographic Code Scanner
            </div>
            <h1 class="hero-h1 font-display">
              Every algorithm.<br/>
              <em style="color:#e879f9">Every dependency. Found.</em>
            </h1>
            <p class="hero-lead">
              IREKAI's Cryptographic Code Scanner performs deep static analysis of your codebase
              to identify every cryptographic primitive, hardcoded algorithm, and quantum-vulnerable
              dependency. The result is a machine-readable Cryptographic Bill of Materials (CBOM)
              and an actionable agility report.
            </p>
            <div class="hero-actions">
              <a href="mailto:info@irekai.nl?subject=Code Scanner Beta" class="btn" style="background:rgba(232,121,249,0.1);border-color:rgba(232,121,249,0.4);color:#e879f9;font-size:0.8rem;padding:0.75rem 1.6rem;">
                Join the beta →
              </a>
              <a href="mailto:info@irekai.nl" class="btn btn-ghost" style="font-size:0.8rem;padding:0.75rem 1.5rem;">
                Request a demo
              </a>
            </div>
          </div>

          <!-- Terminal / scan preview -->
          <div class="terminal-card">
            <div class="terminal-bar">
              <div class="terminal-dots">
                <span style="background:#f87171"></span>
                <span style="background:#fbbf24"></span>
                <span style="background:#34d399"></span>
              </div>
              <div class="terminal-title font-mono">irekai-scan v0.9.0</div>
            </div>
            <div class="terminal-body font-mono">
              <div class="line"><span class="prompt">$</span> irekai-scan --path ./src --output cbom.json</div>
              <div class="line dim">Scanning 2,847 files...</div>
              <div class="line"></div>
              <div class="line green">✓ RSA-2048 found in 14 files</div>
              <div class="line red">✗ AES-128-CBC (deprecated) — 6 locations</div>
              <div class="line red">✗ MD5 hash usage — 3 locations</div>
              <div class="line amber">⚠ EC-P256 — quantum-vulnerable — 22 locations</div>
              <div class="line dim">Found 0 ML-KEM / ML-DSA implementations</div>
              <div class="line"></div>
              <div class="line dim">Generating CBOM...</div>
              <div class="line green">✓ cbom.json written (CycloneDX 1.5)</div>
              <div class="line"></div>
              <div class="line red bold">Crypto Agility Score: 2.1 / 10</div>
              <div class="line red bold">Quantum Risk: CRITICAL</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- What it detects -->
    <section class="detects-section">
      <div class="container">
        <div class="section-label" style="margin-bottom:1.5rem;">Detection capabilities</div>
        <div class="detects-grid">
          <div class="detect-card" v-for="d in detects" :key="d.title">
            <div class="detect-icon" v-html="d.icon"></div>
            <div class="detect-title">{{ d.title }}</div>
            <div class="detect-body">{{ d.body }}</div>
            <div class="detect-examples font-mono">
              <span v-for="e in d.examples" :key="e" class="detect-ex">{{ e }}</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Output -->
    <section class="output-section">
      <div class="container">
        <div class="two-col">
          <div>
            <div class="section-label" style="margin-bottom:1.25rem;">What you receive</div>
            <div class="output-list">
              <div class="output-item" v-for="o in outputs" :key="o.title">
                <div class="output-num font-mono">{{ o.num }}</div>
                <div>
                  <div class="output-title">{{ o.title }}</div>
                  <div class="output-body">{{ o.body }}</div>
                </div>
              </div>
            </div>
          </div>
          <div>
            <div class="section-label" style="margin-bottom:1.25rem;">Supported languages</div>
            <div class="langs-grid">
              <div class="lang-pill font-mono" v-for="l in langs" :key="l">{{ l }}</div>
            </div>
            <div class="section-label" style="margin-top:2rem;margin-bottom:1.25rem;">Integration</div>
            <div class="integ-list">
              <div class="integ" v-for="i in integrations" :key="i">
                <div class="integ-dot"></div>
                <span class="font-mono">{{ i }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Beta signup -->
    <section class="beta-section">
      <div class="container">
        <div class="beta-card">
          <div class="badge" style="background:rgba(232,121,249,0.1);color:#e879f9;border-color:rgba(232,121,249,0.3);margin-bottom:1rem;">
            Private beta
          </div>
          <h3 class="font-display" style="font-size:1.4rem;margin-bottom:0.75rem;">
            Be first to scan your codebase
          </h3>
          <p class="prose" style="margin-bottom:1.5rem;">
            The IREKAI Code Scanner is in active development. Beta participants get early access,
            direct input into the roadmap, and preferential pricing at launch.
          </p>
          <a href="mailto:info@irekai.nl?subject=Code Scanner Beta Access" class="btn" style="background:rgba(232,121,249,0.1);border-color:rgba(232,121,249,0.4);color:#e879f9;font-size:0.8rem;">
            Apply for beta access →
          </a>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const detects = [
  {
    title: 'Deprecated & weak algorithms',
    body: 'Identifies use of MD5, SHA-1, DES, RC4, AES-ECB, RSA < 2048-bit, and other deprecated primitives.',
    examples: ['MD5', 'SHA-1', 'DES', 'RC4'],
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"/><line x1="12" y1="9" x2="12" y2="13"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>`
  },
  {
    title: 'Quantum-vulnerable key exchange',
    body: 'Flags all uses of classical Diffie-Hellman, ECDH, and RSA key exchange that are vulnerable to Shor\'s algorithm.',
    examples: ['RSA', 'ECDH', 'DH', 'ECDSA'],
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>`
  },
  {
    title: 'Hardcoded algorithms & keys',
    body: 'Detects algorithm names, key material, and configuration strings hardcoded into source files — the key blocker to crypto agility.',
    examples: ['"AES-256"', '"rsa"', 'key literals'],
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>`
  },
  {
    title: 'Dependency crypto exposure',
    body: 'Cross-references your SBOM with known cryptographic capabilities of third-party libraries to surface hidden quantum exposure.',
    examples: ['openssl', 'bouncycastle', 'cryptography'],
    icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/></svg>`
  },
]

const outputs = [
  { num:'01', title:'CBOM (CycloneDX 1.5)', body:'Machine-readable Cryptographic Bill of Materials listing every cryptographic asset, its location, and quantum risk classification.' },
  { num:'02', title:'Crypto Agility Score', body:'A composite 0–10 score measuring how easily your codebase can swap cryptographic algorithms, with a per-component breakdown.' },
  { num:'03', title:'Quantum Risk Report',  body:'Ranked list of quantum-vulnerable usage with business impact assessment and prioritised remediation guidance.' },
  { num:'04', title:'CI/CD integration',    body:'Configuration files for GitHub Actions, GitLab CI, and Jenkins to run the scanner on every pull request.' },
]

const langs = ['Python', 'Java', 'Go', 'C / C++', 'JavaScript', 'TypeScript', 'Rust', 'C#', '.NET', 'Kotlin']
const integrations = ['GitHub Actions', 'GitLab CI', 'Jenkins', 'Azure DevOps', 'JIRA (findings)', 'VS Code extension (beta)']
</script>

<style scoped>
.hero-top { display: flex; align-items: center; justify-content: space-between; margin-bottom: 2.5rem; flex-wrap: wrap; gap: 1rem; }
.breadcrumb { font-family: var(--font-mono); font-size: 0.72rem; color: var(--text-dim); text-decoration: none; transition: color 0.15s; }
.breadcrumb:hover { color: var(--text-muted); }

.hero-body { display: grid; grid-template-columns: 1fr; gap: 3rem; align-items: flex-start; }
@media (min-width: 900px) { .hero-body { grid-template-columns: 1fr 400px; } }

.hero-h1 { font-size: clamp(1.9rem, 5vw, 3rem); font-weight: 500; line-height: 1.15; color: var(--text); margin-bottom: 1.25rem; }
.hero-lead { font-size: 1rem; line-height: 1.75; color: var(--text-muted); max-width: 56ch; margin-bottom: 2rem; }
.hero-actions { display: flex; flex-wrap: wrap; gap: 0.75rem; }

/* Terminal */
.terminal-card {
  border-radius: 12px;
  overflow: hidden;
  border: 1px solid var(--border);
  background: #0a0908;
}
.terminal-bar {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.65rem 1rem;
  background: #1a1714;
  border-bottom: 1px solid var(--border);
}
.terminal-dots { display: flex; gap: 0.35rem; }
.terminal-dots span { width: 10px; height: 10px; border-radius: 50%; }
.terminal-title { font-size: 0.65rem; letter-spacing: 0.12em; color: var(--text-dim); }

.terminal-body { padding: 1.25rem; font-size: 0.7rem; line-height: 1.8; }
.line { color: var(--text-muted); }
.line.green  { color: #34d399; }
.line.red    { color: #f87171; }
.line.amber  { color: #fbbf24; }
.line.dim    { color: #57534e; }
.line.bold   { font-weight: 600; }
.prompt { color: #2dd4bf; margin-right: 0.4rem; }

/* Detects */
.detects-section { padding: 4rem 0; border-top: 1px solid var(--border); }
.detects-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 1rem; }
.detect-card {
  padding: 1.4rem;
  border-radius: 12px;
  border: 1px solid rgba(232,121,249,0.15);
  background: rgba(232,121,249,0.03);
  display: flex;
  flex-direction: column;
  gap: 0.65rem;
  transition: border-color 0.2s;
}
.detect-card:hover { border-color: rgba(232,121,249,0.35); }
.detect-icon { width: 22px; height: 22px; color: #e879f9; }
.detect-icon svg { width: 100%; height: 100%; }
.detect-title { font-size: 0.9rem; font-weight: 500; color: var(--text); }
.detect-body { font-size: 0.78rem; line-height: 1.6; color: var(--text-muted); flex: 1; }
.detect-examples { display: flex; flex-wrap: wrap; gap: 0.35rem; }
.detect-ex { font-size: 0.6rem; padding: 0.15rem 0.45rem; border-radius: 3px; background: rgba(232,121,249,0.1); color: #e879f9; border: 1px solid rgba(232,121,249,0.2); }

/* Output */
.output-section { padding: 4rem 0; border-top: 1px solid var(--border); }
.two-col { display: grid; grid-template-columns: 1fr; gap: 3rem; }
@media (min-width: 768px) { .two-col { grid-template-columns: 1fr 1fr; } }

.output-list { display: flex; flex-direction: column; gap: 1.4rem; }
.output-item { display: flex; gap: 1rem; align-items: flex-start; }
.output-num { font-size: 0.6rem; color: #e879f9; opacity: 0.7; min-width: 1.8rem; padding-top: 0.2rem; }
.output-title { font-size: 0.9rem; font-weight: 500; color: var(--text); margin-bottom: 0.25rem; }
.output-body { font-size: 0.82rem; line-height: 1.6; color: var(--text-muted); }

.langs-grid { display: flex; flex-wrap: wrap; gap: 0.5rem; }
.lang-pill { font-size: 0.65rem; padding: 0.25rem 0.65rem; border-radius: 4px; border: 1px solid var(--border); color: var(--text-muted); }

.integ-list { display: flex; flex-direction: column; gap: 0.55rem; }
.integ { display: flex; align-items: center; gap: 0.6rem; }
.integ-dot { width: 5px; height: 5px; border-radius: 50%; background: #e879f9; opacity: 0.7; flex-shrink: 0; }
.integ span { font-size: 0.72rem; color: var(--text-muted); }

/* Beta */
.beta-section { padding: 3rem 0 5rem; }
.beta-card {
  background: rgba(232,121,249,0.03);
  border: 1px solid rgba(232,121,249,0.2);
  border-radius: 14px;
  padding: 2.5rem;
  max-width: 600px;
}
</style>
