<template>
  <footer class="site-footer">
    <div class="container footer-inner">

      <div class="footer-brand">
        <RouterLink to="/" class="footer-logo">
          <svg viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
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
          <span>IREKAI</span>
        </RouterLink>
        <p class="footer-tagline">Cryptographic resilience<br/>for the quantum age.</p>
      </div>

      <nav class="footer-nav">
        <div class="footer-nav-col">
          <div class="footer-nav-label">Products</div>
          <RouterLink to="/products/quantum-readiness"   class="footer-link">Quantum Readiness Assessment</RouterLink>
          <RouterLink to="/products/maturity-model"      class="footer-link">PQC Maturity Model</RouterLink>
          <RouterLink to="/products/supplier-management" class="footer-link">Supplier Management</RouterLink>
          <RouterLink to="/products/code-scanning"       class="footer-link">Code Scanner</RouterLink>
        </div>
        <div class="footer-nav-col">
          <div class="footer-nav-label">Company</div>
          <RouterLink to="/about" class="footer-link">About</RouterLink>
          <a href="mailto:info@irekai.nl" class="footer-link">Contact</a>
          <a href="https://irekai.nl" class="footer-link">irekai.nl</a>
        </div>
      </nav>
    </div>

    <div class="footer-bottom">
      <div class="container footer-bottom-inner">
        <span class="font-mono" style="font-size:0.65rem;color:var(--text-dim);letter-spacing:0.08em;">
          © {{ year }} IREKAI · Post-Quantum Security
        </span>
        <span class="font-mono" style="font-size:0.65rem;color:var(--text-dim);letter-spacing:0.08em;">
          irekai.nl
        </span>
      </div>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>

<style scoped>
.site-footer {
  border-top: 1px solid var(--border);
  margin-top: 6rem;
}

.footer-inner {
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
  padding-top: 3rem;
  padding-bottom: 3rem;
}
@media (min-width: 640px) {
  .footer-inner {
    flex-direction: row;
    justify-content: space-between;
    align-items: flex-start;
  }
}

.footer-brand { display: flex; flex-direction: column; gap: 1rem; }

.footer-logo {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  text-decoration: none;
}
.footer-logo svg { width: 26px; height: 26px; }
.footer-logo span {
  font-family: var(--font-display);
  font-size: 1rem;
  letter-spacing: 0.18em;
  color: var(--text);
}

.footer-tagline {
  font-family: var(--font-mono);
  font-size: 0.7rem;
  line-height: 1.6;
  color: var(--text-dim);
  letter-spacing: 0.04em;
}

.footer-nav {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
}

.footer-nav-col { display: flex; flex-direction: column; gap: 0.6rem; }

.footer-nav-label {
  font-family: var(--font-mono);
  font-size: 0.62rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--text-dim);
  margin-bottom: 0.25rem;
}

.footer-link {
  font-family: var(--font-mono);
  font-size: 0.72rem;
  color: var(--text-muted);
  text-decoration: none;
  transition: color 0.15s;
  letter-spacing: 0.03em;
}
.footer-link:hover { color: var(--text); }

.footer-bottom {
  border-top: 1px solid var(--border-dim);
}
.footer-bottom-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 1rem;
  padding-bottom: 1rem;
}
</style>
