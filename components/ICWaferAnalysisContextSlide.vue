<template>
  <main class="context-page">
    <section class="header">
      <p class="eyebrow">Preliminaries · 2.1</p>
      <h1>IC Wafer Defect Analysis</h1>
      <p class="subtitle">
        Wafer surface quality affects chip reliability, process optimization, and quality control.
      </p>
    </section>

    <section class="main">
      <section class="insight">
        <p class="label">Engineering Insight</p>
        <h2>SEM images reveal wafer defect attributes.</h2>

        <div class="attributes">
          <span>Type</span>
          <span>Location</span>
          <span>Cause</span>
        </div>

        <p class="desc">
          These attributes help engineers understand wafer surface conditions and improve fabrication processes.
        </p>

        <div class="gap">
          <strong>Remaining Gap</strong>
          <p>Scarce data and no unified model for classification, segmentation, and analysis.</p>
        </div>
      </section>

      <section class="methods">
        <p class="label">Traditional Analysis Methods</p>

        <div class="timeline">
          <div class="method">
            <span>01</span>
            <div>
              <strong>Manual feature design</strong>
              <p>Pattern periodicity → handcrafted defect features.</p>
            </div>
          </div>

          <div class="method">
            <span>02</span>
            <div>
              <strong>SVM-based detection</strong>
              <p>Feature space → hyperplane-based class separation.</p>
            </div>
          </div>

          <div class="method">
            <span>03</span>
            <div>
              <strong>CNN-based classification</strong>
              <p>Large datasets → learned visual features for classification and segmentation.</p>
            </div>
          </div>
        </div>
      </section>
    </section>
  </main>
</template>

<style scoped>
.context-page {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 22px 64px;
  overflow: hidden;
  background:
    radial-gradient(circle at 82% 18%, rgba(95, 127, 137, 0.12), transparent 30%),
    radial-gradient(circle at 20% 88%, rgba(95, 127, 137, 0.08), transparent 34%),
    linear-gradient(135deg, #fbfbf8 0%, #eef3f4 58%, #fbfbf8 100%);
  color: #1f2933;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
}

.eyebrow,
.label {
  color: #5f7f89;
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.17em;
  text-transform: uppercase;
}

.eyebrow {
  margin: 0 0 6px;
}

h1 {
  margin: 0;
  color: #314f5a;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 35px;
  line-height: 1.04;
  font-weight: 400;
}

.subtitle {
  margin: 6px 0 0;
  color: #8a9ca3;
  font-size: 12.5px;
}

.main {
  margin-top: 26px;
  display: grid;
  grid-template-columns: 0.82fr 1.18fr;
  gap: 56px;
  align-items: start;
}

.label {
  margin: 0 0 12px;
}

.insight h2 {
  margin: 0;
  max-width: 520px;
  color: #1f2933;
  font-family: Georgia, Cambria, "Times New Roman", serif;
  font-size: 32px;
  line-height: 1.05;
  font-weight: 400;
}

.attributes {
  margin-top: 20px;
  display: flex;
  gap: 10px;
}

.attributes span {
  padding: 8px 14px;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.66);
  border: 1px solid rgba(120, 145, 154, 0.22);
  color: #314f5a;
  font-size: 12px;
  transition: 160ms ease;
}

.attributes span:hover,
.method:hover,
.gap:hover {
  transform: translateY(-3px);
  background: rgba(255, 255, 255, 0.88);
  box-shadow: 0 12px 26px rgba(31, 41, 51, 0.06);
}

.desc {
  margin: 20px 0 0;
  max-width: 500px;
  color: #6b7d86;
  font-size: 12.8px;
  line-height: 1.34;
}

.gap {
  margin-top: 22px;
  padding: 13px 15px;
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.52);
  border-left: 4px solid rgba(95, 127, 137, 0.42);
  transition: 160ms ease;
}

.gap strong {
  display: block;
  color: #1f2933;
  font-size: 13px;
  margin-bottom: 5px;
}

.gap p {
  margin: 0;
  color: #6b7d86;
  font-size: 11.8px;
  line-height: 1.28;
}

.timeline {
  position: relative;
  display: grid;
  gap: 13px;
}

.timeline::before {
  content: "";
  position: absolute;
  left: 15px;
  top: 18px;
  bottom: 18px;
  width: 1px;
  background: rgba(95, 127, 137, 0.28);
}

.method {
  position: relative;
  display: grid;
  grid-template-columns: 42px 1fr;
  gap: 16px;
  align-items: start;
  padding: 10px 0 11px;
  border-bottom: 1px solid rgba(120, 145, 154, 0.18);
  transition: 160ms ease;
}

.method span {
  position: relative;
  z-index: 2;
  width: 31px;
  height: 31px;
  display: grid;
  place-items: center;
  border-radius: 12px;
  background: #e7eef0;
  color: #5f7f89;
  font-size: 10.5px;
}

.method strong {
  color: #1f2933;
  font-size: 13.5px;
  font-weight: 500;
}

.method p {
  margin: 4px 0 0;
  color: #6b7d86;
  font-size: 11.8px;
  line-height: 1.24;
}
</style>